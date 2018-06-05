---
author: tanner_h
date: 2015-04-06 13:47:30+00:00
layout: post
link: http://photodemon.org/1129/photodemon-and-virustotal-com/
slug: photodemon-and-virustotal-com
title: PhotoDemon and VirusTotal.com
excerpt: With every new PhotoDemon release, I receive a flood of emails about the VirusTotal website, and their analysis of the new PhotoDemon build.  After a new release, it is common for several of the site's 60+ scanners to mark PhotoDemon as suspicious.  Before anyone gets too nervous, let's talk about why this occurs, and why I'm not worried about it.

redirect_from:
  - /1129/photodemon-and-virustotal-com/
---

*This article was last updated on 14 May 2018.  If it doesn't match the results you see on VirusTotal, please [let me know](https://github.com/tannerhelland/PhotoDemon/issues) so I can update it again.  Thanks!*

With every new PhotoDemon release, I receive a flood of emails about the [VirusTotal](https://www.virustotal.com/) website, and their analysis of the new PhotoDemon build.  For those who don't know, VirusTotal is a [Google subsidiary](https://en.wikipedia.org/wiki/VirusTotal) that allows users to submit arbitrary files.  VirusTotal will pass your file to dozens of different virus scanners, then provide a nice summary of what each program found.

After a new release, it is common for several of VirusTotal's 60+ scanners to mark PhotoDemon as suspicious.  Before anyone gets too nervous, let's talk about why this occurs, and why I'm not worried about it.

First, let's discuss VirusTotal's methodology.  While there are benefits to VirusTotal's approach - the main one being *convenience* - it is not meant to provide a definitive, scientific approach to malware detection.  VirusTotal's comprehensive scanner selection includes programs from small startups, independent research groups, and foreign companies of many shapes and sizes.  

In recent years, some of the scanners they include do not use malware lists at all, but instead claim to use fancy heuristics like "artifical intelligence" and "real-time threat analysis" to predict malware before humans can.  As of 2018, many of these implementations border on the ridiculous, and they remain extremely prone to false positives.  In fact, VirusTotal explains this in detail on [the About page of their website](https://www.virustotal.com/en/about/):

> Although the detection ratio achieved by the use of multiple antivirus engines/URL scanners is far superior than that offered by just one product, these results DO NOT guarantee the harmlessness of a file/URL. Moreover, **the aggregate amount of false positives of multiple solutions is higher than that of any individual scanner.**

*(emphasis mine)*

Further down the page, there is an entire section dedicated to false positives:

> **False positives**
> 
> **Very often antivirus solutions and URL scanners will produce false positives, i.e. detect as malicious innocuous files and URLs.** These erroneous detections may severely hinder the business activity/popularity of third party products (e.g. refrain access to a given site, disuade users from downloading and installing a given application, etc.).
>
> VirusTotal simply acts as an information aggregator and cannot and will not be held responsible for these false positives. VirusTotal will not whitelist any files or URLs and will not remove any detections resulting from the normal operation of the products it makes use of. False positives should be dealt with the developer/company that offers the product generating the erroneous detection. Links to the sites of the developers/companies of all products/tools used used in VirusTotal can be found in the credits and collaboration acknowledgements section.

*(again, emphasis mine)*

Companies like Microsoft, Apple, and Google have whole teams of people who interface with virus scanner companies, to make sure those scanners don't incorrectly flag their products.  But I am an individual developer who provides PhotoDemon for free.  I work on it in my spare time, and every hour I spend on the phone with a virus-scanner company is an hour not spent improving the program.  I find this very frustrating, and with each passing year, I am less inclined to waste time on this.

To further demonstrate how poor some virus scanners are, here is a link to an empty default project, created using the same programming tools as PhotoDemon:

[Empty Project - 3 kB](media/blank_project.zip)

This program contains no custom source code.  (In fact, I have included the source code files so you can see for yourself - just open them in a text editor like Notepad.)  All the project does is display an empty window, using a default project template.

If I run this totally empty project through VirusTotal this morning, here is what I get:

![VirusTotal results for blank project](media/images/virustotal_blank_project.png) 

For many years now, Avira has been one of the worst offenders for false-positives, so I'm not surprised to see them still screwing up in 2018.  Baidu is more surprising, since you'd expect [the fourth-largest website in the world to do better](https://en.wikipedia.org/wiki/Baidu), but it just goes to show that even massive companies can mess this up.

Despite my endless frustration with low quality virus scanners, I still do my best to work with companies that incorrectly flag PhotoDemon, especially if this is the first time I've had to notify them.  Here is how these email exchanges usually go.  This is the actual text of a past exchange with a virus scanner company, with the company and support individual's names removed, for privacy reasons:

> Dear Tanner,
> 
> Your request has been analyzed. It was a false alarm. The error was fixed.
> 
> Thank you for the cooperation.
> 
> --
> Yours sincerely,
> [Employee name]
> [Company name]
> 
> Category: FALSE ALARM LINK
>
> -------------------Request-------------------------------------
> 
> User sent us a suspicious file.
> User ip: [IP removed]
> User agent: [User agent removed]
> User comment: Hello. I am the developer of an open-source
> editor called "PhotoDemon". Your scanner falsely identifies the PhotoDemon
> download as a BACKDOOR.Trojan virues. I know this is not the case as I
> am the software developer, and I have validated the checksum of the file
> available online, and a freshly compiled copy of the source code.
> 
> Thank you for taking a look at this false positive.
> http://photodemon.org/downloads/PhotoDemon_6.4.zip
> User language: en
> Original file name: SYSTEM:nofile
> File size: 10
> File time: 2015-02-28 17:47:46
> File mime type: text/plain
> MD5: 2da3830a9987dab01efea739e1232d22
> SHA1: b14942eb1cfc0fa193fad2e6ef5f186ff1198219
> 
> --
> = [website link], send-suspic-file.pl v2
> 
> ---------------------------------------------------------------

Seems easy enough, right?  Unfortunately, this is far from a long-term solution.  

When most virus scanner companies are notified of obvious false-positives, all they do is add a file signature to their product's [whitelist](https://en.wikipedia.org/wiki/Whitelisting).  As soon as I release a new version of PhotoDemon - or if I change the current version in any way, like fixing a typo or removing a bug - the program's signature changes, and I have to go through this whole rigamarole again.  

Good companies don't do this - instead, their developers rework the faulty heuristics that led to the false-positive in the first place.  This is great, because indie developers (like me!) only have to contact them once and the problem gets solved forever.  But low-quality scanners simply amass an ever-larger whitelist, and with each new release of a project like PhotoDemon, the cycle repeats.

To that end, I appreciate anyone who can contact these companies for me, and request a closer look at likely false-positives.  This frees me up to spend my time improving PhotoDemon, rather than fighting with malware scanners.

So what's my take-home message?  In my opinion, VirusTotal is most relevant when many scanners report identical results.  If only a small number report a problem - or they report completely *different* problems - it generally indicates a problem with the scanners, and *not* the project you're scanning.  

For new releases of independent, open-source projects like PhotoDemon, recognize that new releases may be flagged simply because they're *new*.  If you wait several days to download an update, VirusTotal results will likely reflect a more "correct" result, since I will have had time to contact the companies involved.

Even with this (lengthy) explanation, I realize that some users remain paranoid about downloading a project that has even 1 hit on VirusTotal.  So let's talk about additional precautions you can take when downloading PhotoDemon or any other open-source software.

First, remember that PhotoDemon is 100% portable.  It does not need to be installed.  It will not modify your PC registry, and it will not modify files outside of its own PhotoDemon folder (unless they are image files that you manually load into the program, of course!).  In fact, you are more than welcome to use a third-party program to verify before- and after- registory snapshots.  [RegShot](http://www.portablefreeware.com/index.php?id=297) is one program that can do this.

Similarly, PhotoDemon never requires administrative rights, so - like most software - you should always use it from inside a non-administrator account.  This provides a system-level failsafe against dangerous behavior.

And let's not forget the coolest thing about open-source projects - that you can review their source code yourself!  There is (literally) nothing to hide in an open-source project like PhotoDemon.  Here is its master source code link:

[https://github.com/tannerhelland/PhotoDemon](https://github.com/tannerhelland/PhotoDemon)

Finally, if you remain concerned about safety, you are always welcome to download the program from a 3rd-party site that performs their own analysis and security guarantee.  These 3rd-party copies may not be as up-to-date as the version available here, but perhaps they will help you feel more comfortable.  For example, here is a link to Softpedia's PhotoDemon download, which they certify as "100% free of spyware, adware, and viruses":

[http://www.softpedia.com/get/Multimedia/Graphic/Graphic-Editors/PhotoDemon.shtml](http://www.softpedia.com/get/Multimedia/Graphic/Graphic-Editors/PhotoDemon.shtml)

Of course, with anything security-related, I should always add a caveat.  PhotoDemon is distributed under a [BSD license](license/).  This popular open-source license means you can use the program however you like, even in a corporate environment, but it is strictly "use at your own risk".  Like most open-source developers, I do everything I can to keep the program bug-free, but I am just one person.  I rely on users to let me know about problems, including possible issues with hacking and malware, so if a time ever comes when many VirusTotal scanners report suspicious behavior with PhotoDemon, you should **absolutely** contact me.

But if the same old low-quality scanners show a problem on VirusTotal, there is not much I can do besides contact their parent companies for the millionth time.  Some companies don't even have websites where developers can submit false-positives (I wonder why?), so I have to use default customer service accounts instead.  In 99% of cases, these accounts ignore developer emails - or if their company *does* listen and fix the problem, they do so without ever notifying me.  

As I mentioned earlier, I also greatly appreciate any kind PhotoDemon users who can contact these companies on my behalf.  Thank you.

I hope this information is helpful.  If you have any additional worries about virus scanners, please [file an issue on GitHub](https://github.com/tannerhelland/PhotoDemon/issues) so I can address it directly.  

