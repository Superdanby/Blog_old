Title: Dealing with Nvidia Optimus
Date: 2017-07-24 18:30
Category: Fedora
Tags: Fedora, Nvidia, Optimus, Negativo17, Bumblebee

Since the release of Fedora 26, Mesa doesn't conflict with Nvidia anymore. Generally, the Nvidia driver can be installed from either [Bumblebee](https://fedoraproject.org/wiki/Bumblebee) or [Negativo17's repo](https://negativo17.org/nvidia-driver/). Both methods are easy to install, but the former one is likely to have more problems.

A small comparison list:

|                        | Bumblebee | Negativo17 |
 ----------------------- | --------- | -----------
| Nvidia Driver Version  | Old       | Up to date |
| Usage                  | Turn on when needed | Always on with Nvidia Optimus |
| Status                 | No updates since 2013 | Still being maintained and has [good support](https://negativo17.org/nvidia-driver/#reply-title) |
| Platform               | Wayland & X | Only on X |


I'd like to have more battery life with my laptop. Thus, Bumblebee seems to be a good choice at first glance. However, there are various issues with it. Some are listed [here](https://fedoraproject.org/wiki/Bumblebee#Troubleshooting), and lots of them are listed [here](https://github.com/Bumblebee-Project/Bumblebee/issues). A major reason is that the Bumblebee project has been lack of support for a **looooong** time. Also Bumblebee is not compatible with [TLP](http://linrunner.de/en/tlp/tlp.html)(I have tried the recommended [fix](http://linrunner.de/en/tlp/docs/tlp-faq.html#nvidia), but in vain.). At last, I gave up on Bumblebee.

But, how can I disable the Nvidia card without Bumblebee? The only way is to prevent the Nvidia modules to load at boot time. After trying for a long time, I came up with the following solution:

-   Create a new Nvidia-enabled entry at the bottom of the Grub menu:
    -   Add a new entry to /etc/grub.d/40_custom. Just simply copy the newest entry from /boot/efi/EFI/fedora/grub.cfg.
-   Disable Nvidia modules on all boot entries except the customized ones:
    -   Add modprobe.blacklist=nvidia,nvidia_drm,nvidia_modeset to GRUB_CMDLINE in /etc/default/grub.

[This script](https://gist.github.com/Superdanby/12ce20158300c378d4e0f196b279d388#file-blacklistnvidia-sh) does the work above.

I've made sure the method above is effective with `tlp-stat`. On my laptop, if the Nvidia card is on, the electric current will not be lower than 1300mA; Otherwise, it can be as low as 750mA.

As of now, my Nvidia card is usually off. And it can be turned on if I boot from the last entry in Grub.
