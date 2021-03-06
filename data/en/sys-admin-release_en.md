<div id="main-page"></div>
# Release Notes for siduction 2014.1.0

We are very happy to present to you the final release of siduction 2014.1.0 -  *Indian Summer* . siduction is a distribution based on  
Debian's unstable branch and we try to release a few new snapshots over the course of each year. For 2014 it will be just this final release.  
We did a lot of stabilizing work in the past year, besides working on further integrating systemd and working on dev releases. We know it is  
not ideal to have an install medium that is older than six months, so please accept our apologies for that, we will try to release more often.<p>  
<p>All our flavours are in pretty good shape, so we will not waste time with an RC and do the real releasse right away.  
<p>siduction 2014.1.0 -  *Indian Summer*  is shipped with six desktop environments: KDE SC, XFCE, LXDE, LXQt, GNOME and Cinnamon, all in 32-  
and 64-bit variants. From the included DEs this time around only LXDE fits on a CD with 700 MegaByte. But as CDs become more irrelevant with  
every day, we are not too worried about this and recommend to use USB-Sticks for installation.

The released images are a snapshot of Debian unstable, that also goes by the name of Sid, from 2014-11-22. They are enhanced with some  
useful packages and scripts, our own installer and a custom patched version of the linux-kernel 3.17, accompanied by X-Server 1.16.1.

Besides those desktop environments we also include  *noX* , which is an environment without X. There is, last, but not least, an image  
that listens to the name of  *Xorg*  and it features the minimal window manager Fluxbox on top of X.

 A year ago we decided to release with  *systemd* , while Debian was still discussing, what init system to use in the future. Meanwhile  
Debian and Ubuntu have decided to go with systemd as well. It is the most technicaly advanced of the init systems at hand. We have a  
preliminary section on systemd in our sidu-manual, which will be expanded and translated to other languages.

### What is new

#### Cinnamon

After our dev release of Cinnamon in October was well received, we are shipping Cinnamon as a full member of the siduction flavour family.  
For further information on the innards of this GTK+ 3 driven desktop environment, please refer to the <a  
href="http://news.siduction.org/2014/10/release-notes-for-sidcution-cinnamon-dev-release/">release notes</a> of that release.

We gain two, we loose one. Razor-Qt is not released by us anymore as it is at it's end of life and merged into LXQt, which we have the pleasure to talk about now, because that is the 2nd addition to our family. With our developer agaida being upstream of LXQt, we will always have the very latest functional packages in our repositories. LXQt has matured a lot and deserves to be part of the family. Even though it has not yet reached the polished swiftness of LXDE, it is on a good way. It has been completely built on Qt 5 and is in large parts prepared for Wayland. 

### And besides that?

#### KDE SC

KDE SC has matured to version 4.14.2, which is one of the last iterations of the KDE 4 chapter. We have taken Kickoff menu out and implemented Homerun instead. Systemsettings has two new modules that debian does (not yet) have. One of them is called 'Desktop Search Advanced and is a more detailed configuration module for Baloo, the successor of Nepomuk. Also, as a second search agent for Baloo besides Dolphin we have integrated Milou into the panel. The other new module in systemsettings is labeled Systemd and ships a plethora of options that can be of tremendous help with configuring the systemd daemon. 

You can safely assume this is the last siduction release shipping software from KDE's fourth cycle. Our next release will ship Frameworks 5  
and Plasma 5.

#### GNOME

GNOME shipped version is 3.14.1 and it brings new things. As GNOME is still pretty new in our release cycle, here is a few hints on how to run it:

There are two ways to start your gnome-session:

*  *GNOME-Classic* , which implements the GNOME2 look
*  *GNOME* , which implements the GNOME 3 look and desktop-effects
To choose GNOME or GNOME-CLASSIC users should choose default session from the display manager menu. By default in live mode GNOME 3 is started but it will use software rendering. To use GNOME 3 with hardware rendering, users of ATI cards must install  *firmware-linux-nonfree*  before starting the installer.
Boot cheatcode "gnome" was removed because it is now deprecated. Windows look in GNOME has changed because GNOME developers dropped minimize and maximize buttons. To minimize or maximize a window, you must use right click in the window title bar and choose minimize or maximize from the menu. Also, to maximize a window you can double click on the window title bar. We have added to Favourites Applications (aka Dash) some of most used applications. You will discover hexchat, transmission, libreoffice, siduction bug report tool, gnome-terminal and many more in Favourites Applications.
</p>
We ship  **noX** , for the second time around, as an official release, which was first introduced in October 2012 as development release. As there is no graphical environment, you need to use  *cli-installer*  as root to run the installation.

 **XFCE**  is still being shipped in version 4.10.1 and is as reliable as ever. It is a desktop environment that just gets out of your way  
when work needs to be done.

Next to  **LXQt**  we also ship the latest version of  **LXDE** , which is also lightweight, but relies on GTK+ 2 instead of Qt. LXDE will  
be developed as long as GTK+ 2 stays usable.

A lot of time consuming changes again went into adapting the codebase we forked to our needs and integration of systemd. Work on the sidu-manual, as it is called now, is ongoing to make it a lot easier to add new content than before.

<p>All in all <a
href="http://bugs.siduction.org/projects/siduction/issues/report">we closed around 230 bugs</a> since the last final release.</p>
 The installer offers  *btrfs*  still as an experimental filesystem. Please be careful if you use it and always backup your data. Also, the installer for now has been reduced to it's basic features until more sophisticated stuff works more reliably. Due to some internal changes in fdisk some parts of the automatic partitioning have to be rewritten. as there was not enough time, we took that feature out for now.

We had to makesome changes to the concept of our artwork. We used to devote each release to a rock song and try to have a matching artwork. For two reasons we gave up on that idea. For one, for a while this year we had no art team at all. On the other hand it takes quite some time to integrate artwork into the infrastructure in it's respective places and make it all work. With the new concept things became a bit easier, all we basicaly need to do is alter the colours or patterns of the given artwork. The distro-art we are using for this and the following releases for the forseeable future was created by Bob, a professional artist. Thanks a lot for your contribution! 

### Our Resources

 [siduction Forum](http://siduction.org) 
 [siduction Blog](http://news.siduction.org) 
 [Git Archive](http://git.siduction.org) 
 [Distro News](http://siduction.org/index.php?module=news) 
 [Bug-Tracker](http://bugs.siduction.org/projects/siduction/issues/new) 
 [siduction-Map](http://bugs.siduction.org/projects/siduction/wiki/Map_Siduction) 
Support can be obtained on our forum as well as on IRC. The relevant channels on OFTC-Network are  *#siduction*  for english support or  *#siduction-core* , ifyou like to join in and participate. On your desktop you also find an icon that takesyou to the right channel for support, depending on the chosen language.

To be able to act as a testbed for Debian, we are introducing our own bug-tracker. Let me explain how you can help us and Debian by submitting bugreports for broken packages. Weathered users will know how to file bugs directly with the Debian BTS(Bug Tracking System). For users not so comfortable with the system we have  *reportbug-ng*  preinstalled.

If you think, you found a bug in a Debian package, please start  *reportbug-ng*  and put the name of the package in the adressline ontop. The app will now search through the already filed bugs for that package and show those. Now it's up to you to determine, if "your" bug has already been reported. Ifit is, ask yourself if you have anything relevant to add to this report or maybe even a patch. If not, you are done for this time. If the bug has not been reported yet and you are not familiar with the BTS yet, you may report the bug in our  
<a href="http://bugs.siduction.org/projects/siduction/issues/new">  
Bug-Tracker.</a>

That obviously goes for siduction packages as well. We will sort the bugs for you and file them in the appropriate place, if it's reproducible. Please look out for a forum post with more detailed info on the bug-tracker soon. If all this seems to complicated for now, feel free to use the bugs-thread on the forum for now, it will keep working until final release.

There is nothing we can tell you about our release cycle other than that we strive for up to four releases per year, but that may vary greatly, depending on developement of siduction and Debian Unstable.

As we are always looking for contributors, here is what to do: Come to IRC to channel  *#siduction-core*  and talk to us about what you would like to do within the project, or where you think you could help. As you will notice if you scroll down, we have  **no art-team**  at the moment. If you are  
willing and capable, talk to us.

### Hardware Tips

If you should own a ATI Radeon graphics accelerator, please use the failsafe option, when booting the Live-ISO. This option will add  
the cheatcodes  *radeon.modeset=0 xmodule=vesa*  to the Kernel bootline, so that you can boot to X. Before installing, on the Live-ISO,  
~~~    
please install firmware-linux-nonfree. To do so, please open your <i>/etc/apt/sources.list.d/debian.list</i> with your favourite editor as root and append <i>contrib non-free</i> to the end of the firstline. Save the edit and do:apt-get update && apt-get install firmware-linux-nonfree If you install the operating system now, the package will be installed also, preventing you from a garbled screen when first rebooting. Mind that if you reboot before installing the system, the changes you made will be lost.

  
~~~

If your system has wireless network, this will probably not work out of the box with free drivers, so you better start with wired network connected. You might want to use the script  *fw-detect*  to get information on wireless drivers. The installer will prompt you for any missing firmware and guide you through the process of installing it.

Last but not least a hint for users of the kernel based virtual machine KVM. The developement of a frontend for the kernel based virtual machine (kvm) has begun as a fork of qemu with the name qemu-kvm or short "kvm". Since qemu version 1.4 all patches of the kvm fork have been integrated back into the qemu source. Also there has been much progress in the field of virtualization. So there is a lot of outdated  
documentation around. We have a current <a  
href="http://wiki.siduction.de/index.php?title=Virtualize_siduction_with_qemu-system-x86_64">worksheet for Qemu in our wiki</a>.  
### Credits for siduction 2014.1.0
  
#### Core Team:
  
Alf Gaida (agaida)  
Angelescu Ovidiu (convbsd)  
Axel Beu (ab)  
Ferdinand Thommes (devil)  
J. Theede (musca)  
Tom Wroblewski (GoingEasy9)  
Torsten Wohlfarth (towo)  
#### Maintainers of the siduction Desktop Environments:
  
 **Cinnamon** : J. Theede (musca)  
 **Gnome** : Angelescu Ovidiu (convbsd)  
 **KDE** : Ferdinand Thommes (devil), Jos?? Manuel Santamar??a Lema (santa)  
 **LXDE** : Alf Gaida (agaida)  
 **LXQt** : Alf Gaida (agaida)  
 **noX** : Alf Gaida (agaida)  
 **XFCE** : Torsten Wohlfarth (towo)  
 **Xorg** : agaida/convbsd  
#### Art Team:
  
Bob  
We  **need**  more contributors for siduction release art!  
#### Code, ideas and support:
  
ayla  
bluelupo  
der_bud  
J. Hamatoma (hama)  
Markus Schimpf (arno911)  
bodhi  
### Thank you!
  
<p>Also thank you very much to all testers and all the people giving us support11  
in any possible way. This is also your achievement.

We also want to thank  **Debian** , as we are using their base.

And now enjoy!
On behalf of the siduction team:
Ferdinand Thommes
</div> <!-- main-page -->
