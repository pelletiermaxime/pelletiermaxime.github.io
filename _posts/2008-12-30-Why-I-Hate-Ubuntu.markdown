---
layout: post
title: Why I hate Ubuntu
---

# {{ page.title }}

I have been clear on <a href="http://identi.ca/pelletiermaxime">identi.ca</a> that I'm using Gentoo and that I don't like 
Ubuntu. After thinking about why I don't like Ubuntu, I came to the conclusion that I *hate* Ubuntu.
Many people asked me to explain why and why I use Gentoo. I won't go into the details of why I love gentoo, because
I understand why it's not a good distro for most users and it isn't a good idea to try to persuade people to switch
from ubuntu. So, here's a list of what I don't like about Ubuntu.

Release cycle
-------------
My first point is about release cycle. As you know, Ubuntu has a new release each 6 months at a fixed date. This means that
they import new applications and packages at the beginning of that cycle and then spend the rest of the time testing
those packages and closing bugs. What this means is that by the time the release is announced, the distro is already old
in my opinion and the only updates for the next 6 months will be security updates. This also has the effect that a lot
of Ubuntu users reinstall each 6 months because they have troubles updating their system to the new release or just don't
know how to update it while keeping all their settings.  
What is more insulting is that Mark Shuttleworth is going in conferences (like he did at aKademy lat year) to ask developers to change their release cycle to match their own. He wants every Linux applications to do their new versions right before the development of new ubuntu begins to make it easier for him. Seriously, as a programmer I find this idea ridiculous. The vast majority of contributors to open source are people doing it in their free time and working on their favorite project when they want. That's why they should release new versions when they feel that their code is stable enough, not when they are forced to. 

Package management / Repositories
---------------------------------
First of all, I have nothing against apt and I really don't care about graphical interfaces around it. What I don't like about Ubuntu is that there is no choice. Of course I understand that it's a binary distro, so the one doing the packages is the one that chooses what option he wants to use to build the software, but that's not a reason to have no options. If I want to install phpmyadmin, maybe I don't want apache with it. Or maybe I want to have sse/sse2/ssse3 on my ffmpeg and x264 packages. I know that people will reply to me that there's repositories for this, but that's exactly my point. Why should I trust external repository that are most of the time untested ? Same for "packages that can't be included for legal reasons". Why do I have to add something like Medibuntu or enable restricted extras repositories ? As far as I know, the first goal of Ubuntu is to be user friendly. Having to look everywhere in forums and wikis to find instructions on how to get mp3 playback isn't user friendly for me. That's why there is tons of "forks" of ubuntu like Linux Mint that aim to be a complete distro out of the box and even provide their own packages. Another thing I hate is when they rename packages or put non friendly names. How are you supposed to know that fglrx is in fact ati video cards drivers ? Why do they rename drivers like xf86-video-via to something like xserver-xorg-video-via instead of keeping the official name over at X.org ?


Contributions (or the lack of)
------------------------------
No matter what some of the ubuntu guys say, Ubuntu is *not* contributing back to upstream. First of all, a big part of their packages are coming from Debian and they don't really contribute back. You can say that all debian contributors also contribute tu Ubuntu, but the contrary is not true at all.
Then there is patches. I can't think of the number of times I have heard developers saying they learned a patch was in ubuntu and that they have never seen it before. Same for backports. Distros that decide to for exemple backport patches from kde 4.2 in kde 4.1 really are screwing the developers. They get bug reports by user using those unsupported versions and they can't do anything about it because they can't know if the problem is in 4.1 or 4.2. Ubuntu supporters are saying that the patchs are all on a big website, but you can't expect every developers to go to each distributions and see their patch. No patch should be used without being posted to upstream's bug tracker and kwowing that the patch is doing the right thing.  
My biggest gripe is that Canonical isn't supporting the kernel or any software really. While Redhat/Novell/IBM/Intel and even Orable contributes massively to the kernel, Ubuntu has not a single full time paid developer working on it as far as I know. I'm pretty sure that they have some developers working on Gnome and 1 on KDE, but that's not enough.  
Same thing on their bug tracker. First of all, their bug tracker is proprietary, so of course that's a major reason for not liking it. But my main complaint is that they are taking the habit of not posting the bugs to upstream's bug tracker, but instead are trying to fix the bug on their own. Also sometimes bugs are turning into a forum about how to fix the problem and finally nothing is being done.


"Flavors"
---------

They chose Gnome as their main desktop environment and even modeled their release cycle on gnome. Their typically release 1 month after a new Gnome release. The problem with that is that kde, xfce, fluxbox, openbox and all other "flavors" have to follow this same cycle and have to release at the same date. This results in a Kubuntu and Xubuntu that are way behind the "main" distribution.

Community
---------

Seriously, this is a mess. I was trying to find information for this article, I and got lost in the wiki, docs and forums, without ever finding what I wanted. In fact, it was detecting my language as french and I couldn't find a way to put it in english and the french docs are of course way behing because they are in a big part only a translation of the english docs.  
Normally I prefer forums because the best users and fans are all there, but the experiences I had in the few months I visited them were really bad. I remember people asking very simple questions like : "What's the apt command to search a package ?". A few hours later, there was something like 25 answers and only the good answer was the 23th. All the other were saying to use the graphical interface or talking about aptitude and other offtopic rambling. I have other exemples that just prove that people reading the forums most of the time don't know what they talk about. At the point that even when I was still using ubuntu, I was visiting the Gentoo forums, which are probably the best linux forums in my opinion because you can be sure that people answering there know their stuff.


In conclusion, i'm sure you can apply most of those points to the majority of distributions. The majority of distros use binary packages and have a fixed release cycle. But their are few distros that in my opinion don't have those issues. Opensuse has a cycle of about 8 months, but they are not afraid to change it if something is wrong. They also support all desktop environments equally and include almost all of them in their dvd. Distributions like Arch and Foresight (based on rpath) manage to be very stable while still have constant new packages and be <a href="http://en.wikipedia.org/wiki/Rolling_release">rolling release distributions</a>. Arch also allow you to customize your packages easily without having to build something from sources with no help. I won't bore you by talking about Gentoo, but of course Gentoo is the ultimate tweaker distribution.  
The main point of this is just to say that I wish the distribution that most of the people new to Linux would be better than this. There must be a way to have a distribution that can be good for the new users (live cd, great installer and graphical package manager and great control panels) while still having the choice of using "unstable" packages, more customization and more teamwork with the application developers and the linux kernel team.

