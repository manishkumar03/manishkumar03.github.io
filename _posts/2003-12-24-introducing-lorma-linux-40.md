---
layout: post
title: "Introducing Lorma Linux 4.0"
date: "2003-12-24"
categories: 
  - "linux"
  - "software"
---

_This article [originally appeared](http://www.osnews.com/story.php?news_id=5499) on Osnews.com._

[Lorma linux 4.0](http://linux.lorma.edu) is the first distribution to be based on Fedora Core, outside of Redhat, that is. It is one of those new breed of single-CD distros that try to include only the best-of-breed applications.

It is primarily a desktop distro and does not include any of the software for setting up http/ftp/mail and other kind of servers. Though the matter of choice vs simplicity is a debatable issue, if you want 5 text editors in addition to OO.org and Koffice, this distro is not for you.

Lorma linux tries to offer what Fedora left out in its release. Redhat users are all too familiar with the process of installing lots of packages after installing the main OS. Its kinda like what you do on Windows only on a smaller scale. But not so with Lorma. Here you get everything that you wish Fedora had included. Don’t get me wrong on this one. I respect the stand taken by Redhat concerning legal issues surrounding mp3 plug-ins and DVD content (un)scrambling systems and other things. But looking at it from an end-user’s perspective, it’s a bit of inconvenience. And that’s exactly what Lorma Linux promises to relieve us from.

I have been using Redhat linux since version 7.1 and my main OS for day-to-day work is Redhat linux 9. I have not used Fedora Core 1 and I don’t plan to do so either. I would definitely be using Fedora Core 2 though. That said; let’s see if how does Lorma linux fare in comparison to Redhat Linux.

**Install:** The install process is identical to that of standard Redhat linux, except one thing. It gives you a choice of 5 package groups, what it calls “Installation Classes’. Different pre-defined package groups will be installed based on what installation class you choose. This approach has its own good and bad points. It’s very good for people who are new to Linux as it saves them the trouble of choosing from thousands of packages. But on the other hand, ‘office workstation’ installation class does not include development tools and the ‘classroom workstation’ installation class includes games!! It should be noted that the users can either accept these pre-defined package groups as it is or they can make changes as they wish by selecting/deselecting packages. Very handy feature. Anyway, the good old custom mode is present too. As any regular reader of OSnews would have guessed that’s what I chose. Install went smoothly, except for one small hiccup which I describe in the support section.

**Multimedia:** This is one of the biggest selling points of this distro. The phrase doesn’t make much sense when you consider that this distro is free but anyway. It comes pre-installed with mp3 plug-in for xmms. Though why they don’t include equalizer presets is beyond me. In fact, none of the distros that I have seen so far include these. It’s a very simple thing to import the presets from winamp and I wish this distro had done so. Maybe in the next version! Mplayer comes with divX and OpenDivX plug-ins pre-installed to watch DVDs ripped in divX format. Among CD writers, k3b has been included which I believe is the best CD burning application in the Linux land.

**Internet:** Mozilla comes with the Modern theme as the default, which looks beautiful compared to that crappy Classic theme and it comes with Flash plug-in pre-installed. These are small things but these are what give the users a better experience. Version 3.1 of Lorma Linux had java pre-installed but it was removed in release 4.0 because of space constraints. I wish they had retained it and removed some other application instead. One candidate for removal could have been Scribus, used for desktop publishing. It is a very specialized application and there are very few people who would be using it in production environment.

Lorma Linux comes with Yahoo messenger pre-loaded for instant messaging. With recent issues regarding gaim and MSN chat rooms access, who knows if Yahoo would also block access to gaim users. I find it very reassuring to have Yahoo messenger ported to Linux as all my friends are not Linux users and most of them use Yahoo messenger anyway. For enjoying streaming audio and video, RealPlayer is present. It is the freeware version and it forces you to register it when you launch it for the first time. I wonder why it does that. I just gave it a dummy mail-id and off I went.

**Support:** Lorma Linux is a project of an educational institution in Philippines. It is not a commercial distro in the true sense. So the basic source of support is the user forums. While I was installing it using VMware, the installer was hanging after installing a few packages. I tried to install it 2 more times but each time it would hang on one package or the other. I posted my problem in the user forum and I had the answer within 5 minutes (I guess it was from one of the developers). Turned out that VMware was using SCSI emulation for the virtual harddisk by default. I changed it to IDE as suggested in the answer to my problem and the install went smoothly. This kind of response is very rare in the freeware world. And I should mention that even I didn’t know at the time of posting the question that I would be doing a review of this distro. So there is no question of favorable treatment or any such thing.

**Office/productivity:** All too familiar OOffice.org is present, version 1.1. Keeping in with the philosophy of single-CD distros, KOffice has not been included, neither is abiWord.

**Misc:** Wine package which was removed in Redhat 9 because of developer constraints is present in Lorma Linux. Though you should be careful while selecting packages if you want to install it. It is present under ‘gaming packages’ and it is the only thing that is present there. As gaming is not the only thing it is used for, it should be present either under ‘System utilities’ or ‘Miscellaneous’. Making it a part of the base package would also be a good thing.

**Cons:** There are lot of places where the installer still uses the word ‘Redhat’. For example, while installing, it gives you a message saying ‘Welcome to Redhat Linux’. There are many more places where it refers to itself as Redhat Linux. Not sure what would be Redhat’s stand on such issues but it should be changed as soon as possible. Synaptic is not present though there is an entry in the start menu. Nothing happens when you click on that. Guess the it got left out during packaging.

**Conclusion:** This distro has a great potential to become a mainstream player only if it gets its target audience well defined. Single-CD distros just don’t have enough room to please everyone. With Redhat itself going after corporate users, Lorma Linux should concentrate more on home users. That means installation classes like ‘office workstation’ have to go. Second thing is that as of now, it is not doing any value addition other than supplying packages missing in Fedora. It would be good if it did something like what Lycoris does. Install the whole CD as an image. With just one CD, the package selection should not be an issue.

Considering the nature of its origin, Lorma Linux people have done a very good job. It can become a serious contender for desktop by taking care of a few things. With Redhat’s polish and Lorma’s package selection, it just can’t go wrong.
