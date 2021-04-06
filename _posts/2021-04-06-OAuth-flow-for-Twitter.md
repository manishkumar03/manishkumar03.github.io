---
layout: post
title: "OAuth flow for Twitter"
date: "2021-04-06"
categories: 
  - "OAuth"
  - "Networking"
  - "Security"
---

When you use the official twitter app, all you have to do is log in with your username and password and off you go. But things are a little different when it comes to third-party twitter clients like Twitterific etc. Twitter does not allow those apps to ask for a user’s login credentials but instead forces them to use OAuth for authorization. And implementing OAuth in an app is a convoluted process. So why force the devs to go through it?

## Why OAuth
The primary reason that sites like Twitter, Facebook, Github etc use OAuth is to allow third-party apps to access a user’s account without getting access to the user’s password. And if a user wants to revoke access for a third-party app, it’s easy to do so and does not require them to change their password.

Twitter uses OAuth 1.0a which is based around cryptographic hash function and does not assume a secure connection whereas the newer and more common OAuth 2.0 standard relies on TLS layer encryption for data security. This article is about OAuth 1.0a.

## How does a cryptographic hash function make data secure
OAuth 1.0a protocol does not assume the network connection to be secure; instead, it relies on a cryptographic hash function (HMAC-SHA1) to verify the data integrity and authenticity of a message. Note that the data isn’t hidden from attackers; it just can’t be modified without the recepient knowing about it.

Let’s see how it works in practice using our old friends [Alice and Bob](https://en.wikipedia.org/wiki/Alice_and_Bob).

Say Alice and Bob want to communicate over an insecure channel. Naturally they don’t want Eve to listen in on their conversations or to modify their messages without them knowing about it. So they agree on a shared secret passphrase in advance which they would use to secure their messages.

1. Alice wants to send the message “Let’s meet for dinner” to Bob. But instead of sending just the message, she computes a hash of the message using their shared secret passphrase and sends both the original message and the hash.
2. Bob is ecstatic on receiving this message but he wants to make sure that
  * it’s indeed Alice who sent the message (sender authentication)
  * the message text he received is what Alice actually wrote (data integrity)
3. So Bob computes the hash of the received message using his copy of the shared secret passphrase. If the hash he computed is same as what Alice sent with her message, then he can be sure that the message indeed came from Alice and that it was not tempered with.
4. If Eve modifies just the message text, the hash computed by Bob won’t match what Alice sent. And if Eve modifies both the message text and the hash, trying to trick Bob into thinking that the modified message came from Alice, the hash calculated by Bob still won’t match because Eve does not have access to the shared secret passphrase.

The specific hashing algorithm used by Twitter is HMAC-SHA1 which outputs a 20-byte hash. The message to be hashed can be of any length. The secret key can also be of any length but it’s recommended that it be at least 20-bytes long. 

*Actual output from this example:*
**Message:** "Let’s meet for dinner"
**Secret Key:** "cvjowpju89xjfsgsferqweq"
**Computed HMAC-SHA1:** "60958fe227b763be7dc7aef7031c356540683e25"

You can see HMAC in action at: <https://www.freeformatter.com/hmac-generator.html>

## Sequence of events
To make this discussion more concrete, let’s assume that a user named Jane has downloaded a third-party twitter client named LittleBirdie.

### Initial setup:
Twitter doesn’t want just any random app to be making reqeusts on a user’s behalf. They have to know who is accessing their API so that they can restrict access if an app doesn’t behave responsibly. So the first thing that LittleBirdie developer has to do is register their app on the Twitter developer dashboard. On successful registration, Twitter will provide an `oauth_consumer_key` and an `oauth_consumer_secret` to the app developer. It’s this `oauth_consumer_secret` that will be used as the secret key to compute the hash.

**Sample `oauth_consumer_key`:** "ftgyFJliiwxBt67213ksEewxU"
**Sample `oauth_consumer_secret`:** "BpWuio7pG7Q367DxEYpyKrMK3beVzBHYuX9e9m5IBkDCgGBUaw"

***Sidenote -*** The consumer key and secret are known by various other names as well, depending on the vendor. Some of the common names are:
>`oauth_consumer_key` === App Key === API Key === Consumer API Key === Consumer Key === Customer Key
>`oauth_consumer_secret` === App Key Secret === API Secret Key === Consumer Secret === Customer Secret

Now for the OAuth 1.0a flow

### First step:
Jane has installed LittleBirdie on her phone. When she runs it for the first time, the app displays a screen with a `Login with Twitter` button. When Jane clicks that button, the app displays a webpage asking Jane to authorize LittleBirdie to access her Twitter account. But before the app can get to that webpage, it has to request Twitter to allow it to display that page. It needs what’s called a `request_token` and that’s where the hashing comes in. The message to be hashed in this case is the `oauth_consumer_key` and the secret to be used for hashing is `oauth_consumer_secret`. So the hashing parameters are:

**message:** `oauth_consumer_key`
**secret key:** `oauth_consumer_secret`

The Twitter endpoint that provides this `request_token` is appropriately named `https://api.twitter.com/oauth/request\_token`. LittleBirdie makes a `POST` request with the hashed `oauth_consumer_key` and if everything checks out, it receives `oauth_token` and `oauth_token_secret`. Ideally these should have been called `request_token` and `request_token_secret` to make their intent clear. In fact, these are the names the app developers generally use to store them. 

The `oauth_consumer_key` and `oauth_consumer_secret` for an app are direct equivalents to username and password for human users. It’s as if the app itself is signing in to Twitter as the first step. This step makes sure that only authorized apps can ask for `request_token`.

**Sample response:**
`oauth_token`=NPcudxy0yU5T3tBzho7iCotZ3cnetKwcTIRlX0iwRl0&`oauth_token_secret`=veNRnAWe6inFuo8o2u8SLLZLjolYDmDP7SzL0YfYI&`oauth_callback_confirmed`=true

### Second step:
Now that LittleBirdie has got the `request_token`, it creates a URL using this token and launches the web browser. If everything checks out, Twitter will display a dialog asking Jane to authorize LittleBirdie so that it can access her Twitter account. The page also displays what kind of access (read-only/read-write etc) the app is requesting. If Jane authorizes LittleBirdie, it will receive the same `request_token` back along with an `oauth_verifier`.

Since this step is browser-based, it can not use hash-based OAuth headers which necessitates one more step for security reasons (the third step detailed below).

**Sample URL:**
https://api.twitter.com/oauth/authorize?`oauth_token`=NPcudxy0yU5T3tBzho7iCotZ3cnetKwcTIRlX0iwRl0

**Sample Response:**
https://yourCallbackUrl.com?`oauth_token`=NPcudxy0yU5T3tBzho7iCotZ3cnetKwcTIRlX0iwRl0&`oauth_verifier`=uw7NjWHT6OJ1MpJOXsHfNxoAhPK

### Third step:
LittleBirdie can now finally request what it wanted all along, i.e. access to Jane’s account. This time, the hashing parameters are:

**message:** `oauth_consumer_key` + `request_token` and `oauth_verifier` received in step 2 above
**secret key:** `oauth_consumer_secret` + `request_token_secret` received in step 1 above

The app now makes a POST request to `https://api.twitter.com/oauth/access\_token` and if everything checks out, it receives a final set of `oauth_token` and `oauth_token_secret`. Ideally these should have been called `access_token` and `access_token_secret` to make their intent clear. In fact, these are the names the app developers generally use to store them. It also receives the user id and screen name for Jane.

**Sample response:**
`oauth_token`=7588892kagSNqWge8gB1WwE3plnFsJHAZVfxWD7Vb57p0b4&`oauth_token_secret`=9veKfYqSryyeKDWz4ebtY3o5ogNLG11WJuZBc9fQrQo

### Final step
LittleBirdie is now all set to interact with Twitter. Say Jane wants to post a tweet. The hashing parameters are:

**message:** `oauth_consumer_key` + `access_token` received in step 3 above
**secret key:** `oauth_consumer_secret` + `access_token_secret` received in step 3 above
**Sample URL:** <https://api.twitter.com/1.1/statuses/update.json?status=hello>

Note that every time Twitter API is accessed, the secret key used to hash the message contains `oauth_consumer_secret` as a component. This makes sure that even if an attacker could get hold of `access_token ` or `access_token_secret ` etc, they cannot use it until they also have `oauth_consumer_secret`. That’s why it’s critically important to keep it safe.