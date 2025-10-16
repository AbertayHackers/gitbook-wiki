# Meltdown & Spectre

By [Sam](broken-reference)

## Vendor Responses

* [ARM](https://developer.arm.com/support/security-update)
* [nvidia](https://nvidia.custhelp.com/app/answers/detail/a_id/4611)
* [AMD](https://www.amd.com/en/corporate/speculative-execution)
* [Intel](https://newsroom.intel.com/wp-content/uploads/sites/11/2018/01/Intel-Analysis-of-Speculative-Execution-Side-Channels.pdf)
* [Genode](https://sourceforge.net/p/genode/mailman/message/36178974/)

## OS Responses

* Microsoft
  * [Windows security updates released January 3 2018 and antivirus software](https://support.microsoft.com/en-us/help/4072699/january-3-2018-windows-security-updates-and-antivirus-software)
  * [Microsoft Intel CPU Vulnerabilities Live Broadcast Meeting](https://join-noam.broadcast.skype.com/microsoft.com/a6ad291111a54963994aec0fe9db158d/en-US/)
* [freebsd](https://www.freebsd.org/news/newsflash.html#event20180104:01)
* [QubesOS](https://github.com/QubesOS/qubes-secpack/blob/master/QSBs/qsb-037-2018.txt)
* [redhat](https://www.redhat.com/en/blog/what-are-meltdown-and-spectre-heres-what-you-need-know)

## Browser Responses

* [Edge & Internet Explorer](https://blogs.windows.com/msedgedev/2018/01/03/speculative-execution-mitigations-microsoft-edge-internet-explorer/)
* [Firefox](https://blog.mozilla.org/security/2018/01/03/mitigations-landing-new-class-timing-attack/)
* [Chromium](https://www.chromium.org/Home/chromium-security/ssca)
* [Webkit](https://webkit.org/blog/8048/what-spectre-and-meltdown-mean-for-webkit/)

## Infrastructure Responses

* [online.net](https://blog.online.net/2018/01/03/important-note-about-the-security-flaw-impacting-arm-intel-hardware/)
* [Elastic](https://www.elastic.co/blog/elastic-cloud-and-meltdown)
* [Wickr](https://www.wickr.com/blog-archive/2018/1/9/lessons-from-a-falling-sky)

## Explainers

* [https://blog.cloudflare.com/meltdown-spectre-non-technical/](https://blog.cloudflare.com/meltdown-spectre-non-technical/)
* [https://danielmiessler.com/blog/simple-explanation-difference-meltdown-spectre/](https://danielmiessler.com/blog/simple-explanation-difference-meltdown-spectre/)
* [https://twitter.com/gsuberland/status/948907452786933762](https://twitter.com/gsuberland/status/948907452786933762)
* [https://www.crowdstrike.com/blog/chip-flaws-spectre-and-meltdown-are-actually-three-vulnerabilities-and-proving-hard-to-mitigate/](https://www.crowdstrike.com/blog/chip-flaws-spectre-and-meltdown-are-actually-three-vulnerabilities-and-proving-hard-to-mitigate/)
* [https://blog.rapid7.com/2018/01/04/meltdown-and-spectre-what-you-need-to-know-cve-2017-5715-cve-2017-5753-cve-2017-5754/](https://blog.rapid7.com/2018/01/04/meltdown-and-spectre-what-you-need-to-know-cve-2017-5715-cve-2017-5753-cve-2017-5754/)

## Performance Impact

* [PCID is now a critical performance/security feature on x86](https://groups.google.com/forum/m/#!topic/mechanical-sympathy/L9mHTbeQLNU)
* [Microsoft - Understanding the performance impact of Spectre and Meltdown mitigations on Windows Systems](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)
* [Measuring OS X Meltdown Patches Performance](https://reverse.put.as/2018/01/07/measuring-osx-meltdown-patches-performance/)

## Detection

* [Endgame](https://www.endgame.com/blog/technical-blog/detecting-spectre-and-meltdown-using-hardware-performance-counters)
* [capsule8](https://capsule8.com/blog/detecting-meltdown-spectre-detecting-cache-side-channels/)

## Proof of Concept

* [https://github.com/mniip/spectre-meltdown-poc](https://github.com/mniip/spectre-meltdown-poc)
* [https://gist.github.com/rootkea/ba370a3c81122030510cfe92cdc5c4a2](https://gist.github.com/rootkea/ba370a3c81122030510cfe92cdc5c4a2)
* [https://github.com/IAIK/meltdown](https://github.com/IAIK/meltdown)

## Press Coverage

* [NYT - Researchers Discover Two Major Flaws in the World’s Computers](https://nytimes.com/2018/01/03/business/computer-flaws.html)
* [threatpost - Vendors Share Patch Updates on Spectre and Meltdown Mitigation Efforts](https://threatpost.com/vendors-share-patch-updates-on-spectre-and-meltdown-mitigation-efforts/129307/)
* [Wired - Triple Meltdown: How so many researchers found a 20-year-old chip flaw at the same time](https://www.wired.com/story/meltdown-spectre-bug-collision-intel-chip-flaw-discovery/)
* [Bloomberg - ‘It Can’t Be True.’ Inside the Semiconductor Industry’s Meltdown](https://www.bloomberg.com/news/articles/2018-01-08/-it-can-t-be-true-inside-the-semiconductor-industry-s-meltdown)
* [techcrunch - How Tier 2 cloud vendors banded together to cope with Spectre and Meltdown](https://techcrunch.com/2018/01/06/how-tier-2-cloud-vendors-banded-together-to-cope-with-spectre-and-meltdown/)
* [Arstechnica - Here’s how, and why, the Spectre and Meltdown patches will hurt performance](https://arstechnica.com/gadgets/2018/01/heres-how-and-why-the-spectre-and-meltdown-patches-will-hurt-performance/)
* [El Reg - IBM melts down fixing Meltdown as processes and patches stutter](https://www.theregister.co.uk/2018/01/09/ibm_meltdown_spectre_patch_issues/)

## Other (Uncategorised)

* [https://lwn.net/Articles/742702/](https://lwn.net/Articles/742702/)
* [https://googleprojectzero.blogspot.co.uk/2018/01/reading-privileged-memory-with-side.html](https://googleprojectzero.blogspot.co.uk/2018/01/reading-privileged-memory-with-side.html)
* [https://github.com/hannob/meltdownspectre-patches](https://github.com/hannob/meltdownspectre-patches)
* [https://www.ncsc.gov.uk/guidance/meltdown-and-spectre-guidance](https://www.ncsc.gov.uk/guidance/meltdown-and-spectre-guidance)
* [https://medium.com/@pwnallthethings/time-travelling-exploits-with-meltdown-1189548f1e1d](https://medium.com/@pwnallthethings/time-travelling-exploits-with-meltdown-1189548f1e1d)
* [https://www.renditioninfosec.com/2018/01/meltdown-and-spectre-vulnerability-slides/](https://www.renditioninfosec.com/2018/01/meltdown-and-spectre-vulnerability-slides/)
* [https://github.com/marcan/speculation-bugs/blob/master/README.md](https://github.com/marcan/speculation-bugs/blob/master/README.md)
* [https://www.peerlyst.com/posts/a-collection-of-links-to-pdfs-of-papers-on-micro-architectural-side-channel-attacks-sorted-by-date-paul-harvey](https://www.peerlyst.com/posts/a-collection-of-links-to-pdfs-of-papers-on-micro-architectural-side-channel-attacks-sorted-by-date-paul-harvey)
* [https://lwn.net/Articles/742999/](https://lwn.net/Articles/742999/)
* [https://www.renditioninfosec.com/2018/01/meltdown-and-sceptre-enterprise-action-plan/](https://www.renditioninfosec.com/2018/01/meltdown-and-sceptre-enterprise-action-plan/)
* [https://plus.google.com/+KristianK%C3%B6hntopp/posts/Ep26AoAZxxd](https://plus.google.com/+KristianK%C3%B6hntopp/posts/Ep26AoAZxxd)
* [https://github.com/lattera/articles/blob/master/infosec/Vulnerabilities/2018-01-05\_Meltdown\_Spectre/article.md](https://github.com/lattera/articles/blob/master/infosec/Vulnerabilities/2018-01-05_Meltdown_Spectre/article.md)
* [https://gist.github.com/woachk/2f86755260f2fee1baf71c90cd6533e9](https://gist.github.com/woachk/2f86755260f2fee1baf71c90cd6533e9)
* [https://isc.sans.edu/diary/23197](https://isc.sans.edu/diary/23197)
* [http://kroah.com/log/blog/2018/01/06/meltdown-status/](http://kroah.com/log/blog/2018/01/06/meltdown-status/)
* [https://medium.com/@sekuryti/meltdown-more-like-letdown-433926f8d743](https://medium.com/@sekuryti/meltdown-more-like-letdown-433926f8d743)
* [https://randomascii.wordpress.com/2018/01/07/finding-a-cpu-design-bug-in-the-xbox-360/](https://randomascii.wordpress.com/2018/01/07/finding-a-cpu-design-bug-in-the-xbox-360/)
* [https://github.com/lgeek/spec\_poc\_arm](https://github.com/lgeek/spec_poc_arm)
* [https://doublepulsar.com/important-information-about-microsoft-meltdown-cpu-security-fixes-antivirus-vendors-and-you-a852ba0292ec](https://doublepulsar.com/important-information-about-microsoft-meltdown-cpu-security-fixes-antivirus-vendors-and-you-a852ba0292ec)
* [http://xlab.tencent.com/special/spectre/spectre\_check.html](http://xlab.tencent.com/special/spectre/spectre_check.html)
* [https://bugs.chromium.org/p/project-zero/issues/detail?id=1272](https://bugs.chromium.org/p/project-zero/issues/detail?id=1272)
* [https://github.com/m8urnett/Windows-Spectre-Meltdown-Mitigations](https://github.com/m8urnett/Windows-Spectre-Meltdown-Mitigations)
* [https://www.enisa.europa.eu/publications/info-notes/meltdown-and-spectre-critical-processor-vulnerabilities](https://www.enisa.europa.eu/publications/info-notes/meltdown-and-spectre-critical-processor-vulnerabilities)
* [https://xorl.wordpress.com/2018/01/10/thoughts-on-meltdown-spectre/](https://xorl.wordpress.com/2018/01/10/thoughts-on-meltdown-spectre/)
* [https://www.reddit.com/r/networking/comments/7o4y40/meltdownspectre\_vulnerability\_tracker/](https://www.reddit.com/r/networking/comments/7o4y40/meltdownspectre_vulnerability_tracker/)
* [https://www.gdatasoftware.com/blog/2018/01/30333-inside-meltdown-spectre](https://www.gdatasoftware.com/blog/2018/01/30333-inside-meltdown-spectre)
