Title: Fedora Installation
Date: 9999-12-29
Category: Fedora
Tags: Fedora, Install

[TOC]

##Preparation

If you're using Windows and wish to install Fedora alongside with it. You can open Disk Management and shrink a drive to make space for Fedora.

Create a live USB with [Fedora Media Writer](https://github.com/MartinBriza/MediaWriter/releases)

##Installation

###Partitioning

Automatic: Anaconda will automatically create mountpoints /, /home, swap with [LVM2](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)).

Custom: This lets you decide which mountpoints to create, the size of each mountpoint, and the partition type. The rest would be handled by Anaconda.

Advanced Custom(Blivet GUI): You'll handle everything by yourself.

###Connecting to the Internet

If you connect to the Internet during the installation process, updates will be downloaded and saved for later use.

###User Creation

You'll have to create exactly one user. There's a checkbox to make the user Administrator.

Also, the root password should be set.

##Post Installation

1.  Enable tap-to-click on your touchpad: Settings > Mouse & Touchpad > Tap to Click
2.  Get new updates: `sudo dnf upgrade`
3.  Settings > Keyboard > Custom Shortcuts: <br/>
    System Monitor: `gnome-system-monitor`, Super + x <br/>
    Terminal: `gnome-terminal`, Ctrl + Alt + T
4.  `sudo dnf install gnome-tweak-tool`
5.  Right click to open terminal from nautilus: `sudo dnf install gnome-terminal-nautilus`
6.  Download Chrome: [https://www.google.com/chrome/browser/desktop/index.html](https://www.google.com/chrome/browser/desktop/index.html) <br/>
    Install Chrome: `sudo dnf install ` *Path to Chrome RPM File*
7.  Git Setup: <br/>
    `git config --global user.name "`*USERNAME*`"` <br/>
    `git config --global user.email "`*EMAIL*`"`
8.  github generate ssh: <br/>
    [https://help.github.com/articles/connecting-to-github-with-ssh/](https://help.github.com/articles/connecting-to-github-with-ssh/)
9.  Download Atom: [https://atom.io/beta](https://atom.io/beta) <br/>
    Install Atom: `sudo dnf install `*Path to Atom RPM File* <br/>
    sync-settings: Install > Search: sync-settings <br/>
    atom-beautify: Replace uncrustify.cfg with <br/> [https://gist.github.com/Superdanby/40de920a0e94c2e8b8389b2a0a34765b](https://gist.github.com/Superdanby/40de920a0e94c2e8b8389b2a0a34765b) <br/>
    autocomplete-clang: `sudo dnf install clang`
10. Download Java: <br/> [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html) <br/>
   Install Java: `sudo dnf install `*Path to Java RPM File* <br/>
   `sudo update-alternatives --config java` <br/>
   `sudo update-alternatives --config javac`
11. [Lollypop Music Player](https://gnumdk.github.io/lollypop-web/): `sudo dnf install lollypop`
12. [VLC Media Player](https://www.videolan.org/vlc/index.html) Setup vlc: <br/>
    `sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm` <br/>
    `sudo dnf install vlc`
13. Setup fstab
14. Setup Graphics Drivers for Nvidia: <br/>
    Install [negativo17 drivers](https://negativo17.org/nvidia-driver/) <br/>
    [Sign the modules](https://superdanby.github.io/Blog/signing-kernel-modules-for-secure-boot.html) (usually nvidia, nvidia_drm, nvidia_modeset) for Secure Boot <br/>
    For battery life optimization, run [BlacklistNvidia.sh](https://gist.github.com/Superdanby/12ce20158300c378d4e0f196b279d388#file-blacklistnvidia-sh) with root privileges to disable Nvidia modules on all boot entries and create a new Nvidia-enabled entry at the bottom of the list. Re-run the script on every kernel updates.
15. `sudo dnf install dolphin`
16. `sudo dnf install wireshark`
17. Install Fedora Media Writer from Software
18. replace .bashrc with [https://gist.github.com/Superdanby/fd864ba673975ca550f013bf3e9c9665](https://gist.github.com/Superdanby/fd864ba673975ca550f013bf3e9c9665)
19. Restore extensions: <br/>
    `sudo dnf copr enable region51/chrome-gnome-shell` <br/>
    `sudo dnf install chrome-gnome-shell`

**Note that the negativo17 drivers have better support than the ones Bumblebee provides. And the Nvidia propriety driver packaged inside is up to date.

**Don't install vlc from negativo17's multimedia repo. It crashes in Wayland.
