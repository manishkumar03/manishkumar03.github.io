---
title: "Mandrake Linux 10 Preview"
date: "2004-01-06"
categories: 
  - "linux"
  - "software"
---

_This article [originally appeared](http://www.osnews.com/story.php?news_id=5577) on Osnews.com._

Mandrake Linux Preview Edition pretty much defines the shape of things to come in Linux land in 2004. With Kernel 2.6, KDE 3.2 beta and XFree86 4.4 beta, it doesn't leave much to be desired. This article refers to cooker snapshot as of December 31, 2003. Please note that this release is not a beta release. This is not even an alpha release. Its just something put together to show what we can expect from Mandrake 10.0. This release comes on only two CDs so some of the packages are missing. And as there are bound to be lot of bugs in this kind of release, I'll be concentrating more on the usability aspect. So let's see if it is worth drooling over.

**Install:**

I did not want burn the iso images to the CDs so I chose to install directly from the harddisk. First thing I did was to bust the iso files using winrar. Then inserted a floppy and double clicked on 'rawwritewin.exe' in directory 'dosutils'. Pointed it to the directory called 'image' and chose 'hdcdrom\_usb.img' . The boot floppy was ready in 4 minutes. All this was done from within Windows. Booted using the boot floppy just created. Chose 'harddisk install' method and pointed the installer to the place where the packages were lying. Note that the installer expects names like hda5 while asking for the package location. It won't understand what C:\\ means. and while busting second iso, make sure that the rpms from this image are extracted in a folder called RPMS2 under 'Mandrake' directory. Otherwise the installer won't be able to find them. The install process itself is essentially same as before. I chose Hindi as one additional language and the installer offered to install 'Devanagiri' keyboard layout. Very helpful. While installing individual packages, the installer does not show the package version number. Not a big deal though but I am used to it from my Redhat days.

I had chosen ext3 as the filesystem and the whole install process took about half an hour. No third party ads were displayed during the install. Even though there is a folder called 'advertising'', it just contains Mandrake's own promotional ads.

**First Boot:**

One of the first thing that hits you when you login is the responsiveness of the system. The system seems really fast. Even though lot of RAM (640 MB DDR) and new Kernel/KDE/XFree86 helps but it certainly is much much faster than Redhat 9 and Windows XP on the same hardware. Sometime I got the creepy feeling that the system was anticipating my mouse movements and bringing up the screens even before I could click! The directory listing of same shared drives (songs etc) was coming up much faster than it was in Windows XP. and these shared drives are FAT32, something Windows is supposed to specialize in. I wonder how would it be when pre-linking is enabled. Hope they add that to the final release.

I have two harddisks, first one containing just the OSes and the second one containing songs, docs, videos etc. The second harddisk has four partitions with volume labels songs, docs, videos and junk. Not only the system automatically mounted all of them under /mnt but get this, it created all the mount points by reading the volume labels of the partitions! I was awesome. No other distro has ever done that. Infact I keep a copy of fstab in a separate partition which I use after installing a new distro. Guess I won't be needing that anymore. Though it mounted my USB harddisk also by itself, it did not read the volume information from that and instead named it as win\_c3.

I had created one normal user account 'manish' during install. When I booted for the first time, the system automatically logged me in as 'manish'. But I wanted to login as root to do some onetime settings. I thought I'll just logout and maybe I'll get to see the login prompt. On logging out, it showed the login prompt but there was no place where I could enter username. I had to click on the name 'manish' but this time it did ask for the password. I Changed some settngs in the login manager and made it show 'root' on the login prompt. I know its not a good idea to display 'root' as one of the users, atleast a text field should have been supplied where I could type username 'root'.

**Package install:**

It turned out that the package 'Wine' got left out during the install. Actually I don't remember seeing it anywhere during the package selection. Anyway, I launched rpmdrake but it ended up in dependency hell. Launched urpmi and gave 'urpmi.addmedia local' and gave it the path for 'Mandrake' directory where the rpm packages were stored. It could not load the rpm package list. Gave an error message saying that the files hdlist and synthesis.hdlist could not be parsed/located even though they were peresent. Mucked around a bit more with urpmi but could not make it access local rpm files. Then stumbled upon the GUI tool called 'Software Media Manager'. The same thing that I was trying to do by command line worked flawlessly in GUI. The local rpm files list got created and finally I was able to install 'Wine'. Well, all I can say is I am yet to find software install nirvana. And I also wonder if it is so tough to put every object file needed in the same rpm package.

**Multimedia:**

This is the first Mandrake release that has got a beep out of my onboard AC97 audio controller. I had to fiddle with audio mixer a bit but it worked in the end. Clicking on a mp3 file brought up totem player. I was hoping to see xmms but nothing a few mouse clicks can't fix. I guess the default should have been xmms in the first place. Xmms here is highly unstable though. It froze up on the first mp3 itself and took the entire system down. But I guess thats ok in this kind of release. And it still does not contain extra skins and equalizer presets.

There are only two media players included, Mplayer and Totem. Xine is not present and neither is libdvdcss even though there is a package present called xine-plugins. Wonder what that does. Video files play by default in totem. I changed the settings to make Mplayer the default for such files. It showed a progress bar saying 'changing system settings'. Clicking on a video file now brought up totem again. Also I had associated dat files (VCD clippings) with Mplayer but it had no effect. It still brings up the dialog box asking me to choose a program. These seem to the problems with KDE rather than with the distro but since KDE itself is beta, you can never be sure.

There are lot of programs installed to deal with image files. Infact, there are too many of them, may be 8 or 9. And all of them do more or less the same thing. Though it is good to have choice, this just seems like overkill to me. Good old Gimp is also present but it is quite old 1.2.5 version. With this kind of release, they could have included 1.3 beta and nobody would have complained. It contains much better menu layout and CYMK support.

**Productivity:**

OO.org 1.1 is present along with KOffice 1.3 beta. Loading time of OO.org has improved a lot since 1.0 but it is still not fast enough. And I think whatever speed gain I saw was because of the new kernel and new XFree86 etc. Filters have also improved for MS Office documents but a lot remains to be done. I opened a simple word document with a few bullet points and all the bullets (in this case, small round dark circles) had big square grey boxes around them. It looked plain ugly. It can ofcourse be fixed but defaults should make sense. KOffice is still very buggy. KWord froze up 2-3 times on opening the same file and just won't get refreshed. Personally, I think these guys should merge with OO.org. There are 7 text editors present, one for each day of the week I guess. Incidentally, I am typing this review in KWrite while playing around with this release.

The menu layout is pretty intuitive for office applications atleast. Instead of grouping them by brand, they are now grouped by functionality. So all the word processors go under 'Wordprocessors'. GNOME dictionary turned out to be very helpful in checking some word meanings but it needs internet connection. It would be much better if there is an offline dictionary included, somethink like Wordweb for Windows.

**Internet:**

Plenty of stuff here. Galeon is also present in addition to Mozilla and Konqueror. And Mozilla still retains its ugly classic theme as default. This point has been talked about so much in online communities but nothing seems to convince the package developers to change it. Flash plugin is not present and neither is Java. What is the point in putting ton of new features in each version if it can't do the basic stuff right? Konqueror was horrible at reproducing the fonts as intended by the web page. I went to www.osnews.com and the page looked terrible in Konqueror. But the same web page looks gorgeous in Mozilla. Maybe there are some font settings that can be changed but default in Konqueror is just hit or miss.

I used gaim to connect to Yahoo chat server and everything worked right the first time. There is an application called 'Screem' to build web sites. Its something similar to Yahoo site builder though not that powerful or that intuitive. I could not find site templates which is the first thing it should have had.

In terms of internet security, the system has a firewall called Shorewall. I chose the standard level of security accepting the default settings. The Zone alarm firewall test on Windows XP shows all the ports to be in stealth mode. Means that it eats up all the incoming ICMP packets and it appears that there is no PC at this IP address. I decided to see how does Shorewall fare. Went to the site 'http://scan.sygate.com' and gave a port scan. It showed all the ports to be in 'closed' state only. That means that someone could still see that there is a PC at this IP address. It is secure but I won't have worried had it been in 'stealth' mode. I then changed the security level to 'paranoid' and sure enough, the port were shown to be 'Blocked' which means they are in stealth mode. I felt better but now I could not access my shared drives mounted under /mnt. Oh well..

Did a Nmap scan also on the PC and it showed only port 6000 to be open which was being used by X11.

**General usability:**

One of my pet peeves is the default application bindings in Linux distros for the common type of files and Mandrake doesn't fare any better than others. eg double-clicking on an iso image file brings up an application selection dialog. Now the most common use of an iso file is to burn it on to a CD and K3b should have been configured to do so by default. Xandros does this right. Another example is .dat files. There are used in VCDs. Now the only thing I can do with a dat file is to view it. So Mplayer should have got fired up and played the movie. Since this is just a preview release, maybe the things will change in future. Moreover with all the distros having more or less the same standard set of packages, these are the only areas where a distro can differentiate itself from others. I am sure we'll be seeing a lot of usability enhancements in 2004.

The system seems stable enough for daily use. The only two things that were acting up were xmms and KOffice. Everything else seems to be working fine. I would like to say here that the speed of the system reduced a bit after using it for 2-3 days. Maybe because of all those log files getting written.

**Conclusion:**

This is going to be a big release for Mandrake especially considering their financial situation. It won't be wrong to say that this is the release that can make them or break them. Hope they get this one right. Enough has been written about KDE 3.2 beta and how it still needs a lot of polish. As for me, I'll be giving Fedora core 2 a spin and then decide for myself. If Fedora offers same levels of performance, I don't mind installing a few multimedia packages and getting on with my work.
