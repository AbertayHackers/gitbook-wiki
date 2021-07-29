# MacOS

## Intro/links/basics

* [A basic intro](http://www.macforbeginners.com/osx-guide/mac-os-x-introduction/)
* [Security & Privacy Guide](https://github.com/drduh/macOS-Security-and-Privacy-Guide)
* [Awesome commands](https://github.com/herrbischoff/awesome-osx-command-line) like default TextEdit to plain text
* [launchd.info](http://www.launchd.info/) “A launchd Tutorial”

## Apple Documentation

* [Security updates list](https://support.apple.com/en-gb/HT201222)
* [WWDC Privacy and Security sessions](https://developer.apple.com/videos/frameworks/privacy-and-security) \(Videos\)

## General

### iCloud

* Adding `.nosync` to the end of a folder in iCloud Drive stops it being synced \(via [@jimconacher](https://twitter.com/jimconacher)\).

### .zshprofile

macOS Catalina and later ship with `zsh` as [the default shell](https://support.apple.com/en-us/HT208050).

* [Moving to Zsh](https://scriptingosx.com/2019/06/moving-to-zsh/) - [Armin Briegel](https://twitter.com/titanonearth)

### .hushlogin

Add a `.hushlogin` file to the directory you terminal starts in to suppress the `Last login:` message at the top of your terminal.

```text
touch .hushlogin
```

### Lock Screen

#### Change Key Combo

Go to `System Preferences` &gt; `Keyboard` &gt; `Shortcuts` &gt; `App Shortcuts`

Click `+` to add a new one called `Lock Screen` and set the key combo \(eg. `⌥⌘+L`\)

#### Stop Wifi Dropping on Screen Lock

```text
cd /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/
sudo ./airport en0 prefs DisconnectOnLogout=NO
```

### Disk Images

* [Understanding DMG Files](https://www.blackbagtech.com/blog/2011/04/15/understanding-dmg-files-part-1-of-3/)
* [Sparse Bundles Defined](http://www.thexlab.com/faqs/sparsebundledefined.html)

### Random

* [How to Fix Slow SMB File Transfers on OS X](https://dpron.com/os-x-10-11-5-slow-smb/) - [Dan Roncadin](https://twitter.com/dpron)

## Homebrew

[Homebrew](https://brew.sh/) \(`brew`\) is a package manager for macOS akin to the [Advanced Package Tool](https://wiki.debian.org/Apt) \(`apt`\) on Debian and Ubuntu.

### Taps

[Taps](https://docs.brew.sh/Taps) are third party repositories for homebrew.

* [sidaf/homebrew-pentest](https://github.com/sidaf/homebrew-pentest) “penetration testing related tools”

#### Example

If you run `brew tap sidaf/homebrew-pentest` you'll be able to install any formulas from the `sidaf/homebrew-pentest` repository via `brew install`. `brew install panoptic` will search the default Homebrew repository then any tapped repositories for a formula with the name `panoptic`.

### Python

As of Homebrew [1.5.0](https://brew.sh/2018/01/19/homebrew-1.5.0/) `brew install python` installs `python3.x` **not** `python2.7.x`. This was not [PEP 394](https://www.python.org/dev/peps/pep-0394/) compliant as running `python` would execute the `python3.x` binary which violates “all distributions should ensure that `python` refers to the same target as `python2`”.

This was fixed in [1.6.0](https://brew.sh/2018/04/09/homebrew-1.6.0/). `brew install python` still installs `python3.x` but will not symlink `python` to the `python3.x` binary. Running `python` will execute the system `python2.7.x` binary and running `python3` will execute the brew `python3.x` binary.

See [Homebrew and Python ](https://docs.brew.sh/Homebrew-and-Python) for more info.

### Upgrading Packages

By default Homebrew **does not** automatically update itself or installed packages. To manually update Homebrew and upgrade all installed packages run:

1. `brew update` \(Update the formulae and Homebrew itself\)
2. `brew upgrade` \(Upgrade all packages installed by Homebrew\)

By default, Homebrew **does not** uninstall old versions of formula. From time to time you'll want to run `brew cleanup` to remove old version of formula.

See [FAQ](https://docs.brew.sh/FAQ) for more info.

## Virtualisation

#### VMWare Fusion

We get [VMWare Fusion](https://www.vmware.com/products/fusion.html) free from [VMWare DreamSpark](https://vmapss.onthehub.com/WebStore/Welcome.aspx). Used by most mac wankers on the course. Would recommend over all other virtualisation programs for Mac.

Currently [does not work with M1 Macs](https://blogs.vmware.com/teamfusion/2021/04/fusion-on-apple-silicon-progress-update.html).

#### Parallels

[Parallels](https://www.parallels.com/uk/products/desktop/)

## Apps

### General

* [Amphetamine](https://github.com/x74353/Amphetamine) \([ App Store](https://itunes.apple.com/gb/app/amphetamine/id937984704)\) - This app keeps your Mac awake for a set period of time, whilst an app is running, and much more.
* [The Unarchiver](https://theunarchiver.com/) \([ App Store ](https://itunes.apple.com/us/app/the-unarchiver/id425424353?mt=12)\) Open any archive in seconds
* [Rocket](https://matthewpalmer.net/rocket/) Slack-style emoji picker for your Mac
* [Texpad](https://www.texpad.com/osx) Native Mac OS app with efficient LaTeX environment
* [DiskMaker X](http://diskmakerx.com/) Build an OS X boot disk
* [BitBar](https://getbitbar.com/) Put anything in your menu bar
* [DiscreteScroll](https://github.com/emreyolcu/discrete-scroll/releases) Stop the annoying mouse acceleration when scrolling in macOS

### Programming

For general information see [Programmming](../../programming-scripting/tools.md). This section list macOS specific tools.

* [Xcode](https://developer.apple.com/xcode/) \([ App Store ](https://itunes.apple.com/us/app/xcode/id497799835)\) Apple's own IDE. Best for [C](../../programming-scripting/c-coding.md), C++ and Objective-C.
* [Quiver](http://happenapps.com/#quiver) \([ App Store](https://itunes.apple.com/app/quiver-programmers-notebook/id866773894)\) notebook built for programmers
* [Dash](https://kapeli.com/dash) offline access to 200+ API documentation sets

### Security/ Privacy

* [1Password](https://1password.com/) \([ App Store ](https://itunes.apple.com/us/app/1password/id443987910)\) Apple device focused password manager
* [Little Snitch](https://www.obdev.at/products/littlesnitch/index.html) Application firewall
* [GPGTools/ GPG Suite](https://gpgtools.org/) “Use GPG Suite to encrypt, decrypt, sign and verify files or messages”
* [Privileges.app](https://github.com/SAP/macOS-enterprise-privileges) “providing a quick and easy way to get administrator rights when needed”

#### Objective-See

[Objective-See](https://objective-see.com/index.html) was created by [Patrick Wardle](https://twitter.com/patrickwardle) to provide simple, effective and free macOS security tools. Some of his most useful tools are listed below.

* [BlockBlock](https://objective-see.com/products/blockblock.html) \(_Beta_\) Alerts when something is persistently installed
* [OverSight](https://objective-see.com/products/oversight.html) Monitors and alerts on mic and webcam access
* [LuLu](https://objective-see.com/products/lulu.html) Open-source application firewall 
* [What's Your Sign?](https://objective-see.com/products/whatsyoursign.html) Adds a menu item to Finder.app to view the cryptographic signature of files

### Touch Bar

* [HapticKey](https://github.com/niw/HapticKey) “trigger haptic feedback when tapping Touch Bar”

## Research

* [Papers, Slides and Thesis Archive](https://papers.put.as/macosx/macosx/) - [osxreverser](https://twitter.com/osxreverser)
* [osx-security-awesome](https://github.com/kai5263499/osx-security-awesome) “collection of OSX and iOS security resources”
* [mac-white-papers](https://github.com/0xmachos/mac-white-papers) "Every OS X/ macOS white paper"

### Blogs

* [The Eclectic Light Company](https://eclecticlight.co/category/macs/) - [Howard Oakley](https://twitter.com/howardnoakley) \(Security, General\)
* [mac4n6](https://www.mac4n6.com/) - [Sarah Edwards](https://twitter.com/iamevltwin) \(Forensics\)
* [Objective-See](https://objective-see.com/blog.html) - [Patrick Wardle](https://twitter.com/patrickwardle) \(Security\)
* [derflounder](https://derflounder.wordpress.com/) - [Rich Trouton](https://twitter.com/rtrouton) \(General, Security\)
* [theevilbit](https://theevilbit.github.io/posts/) - [Csaba Fitzl](https://twitter.com/theevilbit)\(Security\)

### Talks

#### Older

* [Thunderstrike: EFI bootkits for Apple MacBooks](https://media.ccc.de/v/31c3_-_6128_-_en_-_saal_1_-_201412291830_-_thunderstrike_efi_bootkits_for_apple_macbooks_-_trammell_hudson) - [Trammell Hudson](https://twitter.com/qrs) [Annotated Slides](https://trmm.net/Thunderstrike_31c3) \(31c3\)
* [De Mysteriis Dom Jobsivs: Mac EFI Rootkits](https://www.youtube.com/watch?v=W21ZIaKf5HA) - [snare](https://twitter.com/snare) [Slides](https://media.blackhat.com/bh-us-12/Briefings/Loukas_K/BH_US_12_LoukasK_De_Mysteriis_Dom_Jobsivs_Slides.pdf) \(Black Hat 2012\)

#### 2015

* [Stick That In Your \(root\)Pipe & Smoke It](https://vimeo.com/147887652) - [Patrick Wardle](https://twitter.com/patrickwardle) \(Ekoparty 2015\)
* [ThunderStrike 2: Sith Strike](https://www.youtube.com/watch?v=xxl5xOQxXOk) - [Xeno Kovah](https://twitter.com/XenoKovah) [Slides](http://www.legbacore.com/Research_files/TS2-HITB_GSEC.pdf) \(HITBGSEC 2015\)
* [ThunderStrike 2: Sith Strike](https://www.youtube.com/watch?v=CtEdfMP6rJo) - [Trammell Hudson](https://twitter.com/qrs), [Xeno Kovah](https://twitter.com/XenoKovah) & [Corey Kallenberg](https://twitter.com/coreykal) [Annotated Slides](https://trmm.net/Thunderstrike2_details) \(Black Hat 2015\)
* [DLL Hijacking on OS X](https://www.youtube.com/watch?v=PGVNja2MNws) - [Patrick Wardle](https://twitter.com/patrickwardle) [Slides](https://s3.amazonaws.com/s3.synack.com/canSecW.pdf) \(DEFCON 23\)

#### 2016

* [The Apple Sandbox: Deeper Into The Quagmire](https://www.youtube.com/watch?v=mG715HcDgO8) - [Jonathan Levin](https://twitter.com/Morpheus______) [Slides](http://newosxbook.com/files/HITSB.pdf) \(HITBGSEC 2016\)
* [I've got 99 Problems, but LittleSnitch ain't one](https://www.youtube.com/watch?v=sRcHt-sxcPI) - [Patrick Wardle](https://twitter.com/patrickwardle) [Slides](https://speakerd.s3.amazonaws.com/presentations/881b7cc511b34f73a6009d4c4e3ac2ad/DefCon_2016.pdf) \(DEFCON 24\)
* [Thunderstrike 2](https://www.youtube.com/watch?v=B3vQCaak1EI) - [Trammell Hudson](https://twitter.com/qrs) \(CITP Princeton\)

#### 2017

* [The Apple of your EFI](https://www.youtube.com/watch?v=VT7WwAyOCXI) - [Rich Smith](http://twitter.com/iodboi) and [Pepijn Bruienne](https://twitter.com/bruienne) \(Ekoparty 2017\)
* [Oversight: Exposing Spies On MacOS](https://www.youtube.com/watch?v=xsDGozG5t9A) - [Patrick Wardle](https://twitter.com/patrickwardle) \(HITBAMS 2017\)

#### 2018

* [A Deep Dive into macOS MDM](https://www.youtube.com/watch?v=ku8jZe-MHUU) - [Jesse Endahl](https://twitter.com/jesseendahl) & [Max Bélanger](https://twitter.com/maxbelanger) [Slides](https://www.dropbox.com/s/8gcuckiwfcmjsr5/us-18-Endahl-A-Deep-Dive-Into-macOS-MDM-And-How-It-Can-Be-Compromised.pdf) \(Black Hat 2018\)
* [Fire & Ice: Making and Breaking macOS Firewalls](https://www.youtube.com/watch?v=UANF2FQctDg) - [Patrick Wardle](https://twitter.com/patrickwardle) [Slides](https://speakerdeck.com/patrickwardle/fire-and-ice-making-and-breaking-macos-firewalls) \(Black Hat 2018\)
* [The Mouse is Mightier than the Sword](https://www.youtube.com/watch?v=gLrB7enpbiw) - [Patrick Wardle](https://twitter.com/patrickwardle) [Slides](https://media.defcon.org/DEF%20CON%2026/DEF%20CON%2026%20presentations/Patrick%20Wardle/DEFCON-26-Patrick-Wardle-The-Mouse-Is-Mightier-Synthetic0Reality.pdf) \(DEFCON 26\)

### Slides

* [The Apple Sandbox](https://media.blackhat.com/bh-dc-11/Blazakis/BlackHat_DC_2011_Blazakis_Apple%20Sandbox-Slides.pdf) - Dionysus Blazakis \(No video\)
* [OS X El Capitan sinking the S\H/IP](https://papers.put.as/papers/macosx/2016/syscan360stefanesserosxelcapitansinkingtheship.pdf) - [Stefan Esser](https://twitter.com/i0n1c) \(No video\)
* [Code Signing – Hashed Out](http://www.newosxbook.com/articles/CodeSigning.pdf) - [Jonathan Levin](https://twitter.com/Morpheus______) \(No video\)

### Articles

* [The Evolution of Mac OS X Security and Privacy Features](https://www.intego.com/mac-security-blog/mac-os-x-security-features-timeline/) - Joshua Long \(Intego Mac Security Blog\)
* [Booting Secure](https://michaellynn.github.io/2018/07/27/booting-secure/) - [Michael Lynn](https://twitter.com/mikeymikey) On Mac Secure Boot
* [Apple iMac Pro and Secure Storage](https://duo.com/blog/apple-imac-pro-and-secure-storage) - Pepijn Bruienne \(Duo Blog\)
* [Bypass macOS rootless by sandboxing](https://medium.com/0xcc/bypass-macos-rootless-by-sandboxing-5e24cca744be) - [CodeColorist](https://twitter.com/CodeColorist)
* [Creating signed and customized backdoored macOS applications](https://medium.com/@adam.toscher/creating-signed-and-customized-backdoored-macos-applications-by-abusing-apple-developer-tools-b4cbf1a98187) - [Adam Toscher](https://twitter.com/W00Tock)
* [Leveraging Emond on macOS For Persistence](https://posts.specterops.io/leveraging-emond-on-macos-for-persistence-a040a2785124) - [Christopher Ross](https://twitter.com/xorrior) \(SpecterOps\)
* [macOS 10.13.1 insecure cron system](https://m4.rkw.io/blog/macos-high-sierra-10131-insecure-cron-system.html) - Mark Wadham
* [Load & Execute Bundles with migrationTool](https://posts.specterops.io/load-execute-bundles-with-migrationtool-f952e276e1a6?gi=8d4811ed1eb0) - [Christopher Ross](https://twitter.com/xorrior) \(SpecterOps\)
* [MacOS monitoring the open source way](https://blogs.dropbox.com/tech/2018/04/4696/) - Michael George \(Dropbox Blog\)
* [Little Snitch Detection in Malware](https://bitrot.sh/post/24-12-2017-little-snitch/) - [bitsrot](https://twitter.com/bitsrot)
* [A useless analysis of macOS \(OS X\) release dates](https://robservatory.com/a-useless-analysis-of-os-x-release-dates/) - [Rob Griffiths](https://twitter.com/rgriff)
* [Encrypting for Apple's Secure Enclave](https://darthnull.org/security/2018/05/31/secure-enclave-ecies/) - [David Schuetz](https://twitter.com/darthnull)
* [The Empire Strikes Back Apple](https://reverse.put.as/2015/05/29/the-empire-strikes-back-apple-how-your-mac-firmware-security-is-completely-broken/) - [osxreverser](https://twitter.com/osxreverser)
* [macOS FileVault2 Password Retrieval](http://blog.frizk.net/2016/12/filevault-password-retrieval.html) - [Ulf Frisk](https://twitter.com/UlfFrisk)
* [Escaping the Sandbox – MS Office on MacOS](https://www.mdsec.co.uk/2018/08/escaping-the-sandbox-microsoft-office-on-macos/) - MDSec
* [task\_t considered harmful](https://googleprojectzero.blogspot.com/2016/10/taskt-considered-harmful.html) - [Ian Beer](https://twitter.com/i41nbeer) \(Project Zero Blog\)
* [Reverse Engineering macOS High Sierra Supplemental Update](https://cocoaengineering.com/2017/10/08/reverse-engineering-macos-high-sierra-supplemental-update/) - [Daniel Martín](https://twitter.com/dmartincy/)
* [Password Cracking AES-256 DMGs and Epic Self-Pwnage](https://www.whitehatsec.com/blog/cracking-aes-256-dmgs-and-epic-self-pwnage/) - [Jeremiah Grossman](https://twitter.com/jeremiahg)
* [The Apple of Your EFI: Mac Firmware Security Research](https://duo.com/blog/the-apple-of-your-efi-mac-firmware-security-research) - [Rich Smith](http://twitter.com/iodboi) and [Pepijn Bruienne](https://twitter.com/bruienne) \(Duo Blog\)

### Papers

* [The Apple Sandbox](https://dl.packetstormsecurity.net/papers/general/apple-sandbox.pdf) - Dionysus Blazakis \(2011\)
* [De Mysteriis Dom Jobsivs: Mac EFI Rootkits](http://ho.ax/De_Mysteriis_Dom_Jobsivs_Black_Hat_Paper.pdf) - [snare](https://twitter.com/snare) \(2012\)
* [Dylib hijacking on OS X](https://www.virusbulletin.com/uploads/pdf/magazine/2015/vb201503-dylib-hijacking.pdf) - [Patrick Wardle](https://twitter.com/patrickwardle) \(2015\)
* [A Deep Dive into macOS MDM](https://www.dropbox.com/s/d5ikab99q7h3aga/us-18-Endahl-A-Deep-Dive-Into-macOS-MDM-And-How-It-Can-Be-Compromised-wp.pdf) - [Jesse Endahl](https://twitter.com/jesseendahl) & [Max Bélanger](https://twitter.com/maxbelanger) \(2018\)

### Forensics

* [Detection of Backdating the System Clock in macOS](http://cyberforensicator.com/2018/01/21/detection-of-backdating-the-system-clock-in-macos/) - [Igor Mikhaylov](https://twitter.com/Weare4n6)
* [How to mount Mac APFS images in Windows](https://az4n6.blogspot.com/2018/01/how-to-mount-mac-apfs-images-in-windows.html) - [Mari Degrazia](https://twitter.com/maridegrazia)
* [Mounting an APFS image in Linux](https://az4n6.blogspot.com/2018/01/mounting-apfs-image-in-linux.html) - [Mari Degrazia](https://twitter.com/maridegrazia)
* [I Know What You Did Last Month: A New Artifact of Execution on macOS 10.13](https://www.crowdstrike.com/blog/i-know-what-you-did-last-month-a-new-artifact-of-execution-on-macos-10-13/) - Kshitij Kumar and Jai Musunuri \(CrowdStrike Blog\)
* [Introducing Unified Logging](https://www.mac4n6.com/blog/2016/11/13/new-macos-sierra-1012-forensic-artifacts-introducing-unified-logging%20) - [Sarah Edwards](https://twitter.com/iamevltwin%20)

### Exploits

* [DYLD\_ROOT\_PATH vulnerability](https://github.com/luismiras/muymacho) \(10.10.5\)
* [task\_t considered harmful](https://bugs.chromium.org/p/project-zero/issues/attachmentText?aid=256266) - [Ian Beer](https://twitter.com/i41nbeer) \(10.11.5\) \(10.12\)

## Books

* [Mac OS X Internals: A Systems Approach](http://osxbook.com/) - Amit Singh \(2006\)
* \[The Mac Hacker's Handbook\]\(\[[https://www.wiley.com/en-us/The+Mac+Hacker's+Handbook-p-9780470395363\]\(https://www.wiley.com/en-us/The+Mac+Hacker's+Handbook-p-9780470395363\)\](https://www.wiley.com/en-us/The+Mac+Hacker's+Handbook-p-9780470395363]%28https://www.wiley.com/en-us/The+Mac+Hacker's+Handbook-p-9780470395363%29\)\) - [Charlie Miller](https://twitter.com/0xcharlie) and [Dino Dai Zovi](https://twitter.com/dinodaizovi) \([ Amazon](https://www.amazon.co.uk/Mac-Hackers-Handbook-Charlie-Miller/dp/0470395362)\) \(2009\)
* [Mac OS X and iOS Internals](http://www.wrox.com/WileyCDA/WroxTitle/Mac-OS-X-and-iOS-Internals-To-the-Apple-s-Core.productCd-1118057651.html) - [Jonathan Levin](https://twitter.com/Morpheus______) \([ Amazon](https://www.amazon.co.uk/Mac-OS-IOS-Internals-Programmer/dp/1118057651)\) \([ Legit PDF](http://newosxbook.com/MOXiI.pdf)\) \(2012\)

### MacOS and iOS Internals \(Levin\)

* [MacOS and iOS Internals, Volume I - User Mode](http://newosxbook.com/index.php) - [Jonathan Levin](https://twitter.com/Morpheus______) \([ Amazon](https://www.amazon.com/MacOS-iOS-Internals-User-Mode/dp/099105556X)\) \(2017\)
* [MacOS and iOS Internals, Volume III: Security & Insecurity](http://newosxbook.com/index.php) - [Jonathan Levin](https://twitter.com/Morpheus______) \([ Amazon ](https://www.amazon.com/MacOS-iOS-Internals-III-Insecurity/dp/0991055535)\) \(2016\)

