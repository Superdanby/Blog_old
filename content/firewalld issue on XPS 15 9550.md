Title: XPS 15 9550 issues with Fedora 25
Date: 2017-3-9 11:00
Category: System
Tags: Yee, Yeee

## Firewalld fails to stop when shutting down.


### ![Current Workaround](https://bugzilla.redhat.com/show_bug.cgi?id=1397274)

Set CleanupOnExit=no in /etc/firewalld/firewalld.conf

<br>

## ![Bluetooth not seeing any devices](http://fedoraproject.org/wiki/Fedora_Tested_Laptops:Dell_XPS_15_9550_FHD).

### Current Workaround

`sudo dnf install linux-firmware` (?)
