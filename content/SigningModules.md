Title: Signing Modules to Secure Boot
Date: 2017-05-25 13:46:00
Category: Fedora
Tags: Fedora, Yee, Secure Boot

[TOC]

##Key Creation

###Create Signing Keys
`openssl req -new -x509 -newkey rsa:2048 -keyout MOV.priv -outform DER -out MOK.der -nodes -days 36500 -subj "/CN=Descriptive name/"`

###Sign the Module
`sudo /usr/src/kernels/$(uname -r)/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n ` *MODULE_NAME* ` )`

###Register the Keys to Secure Boot
`sudo mokutil --import MOK.der`
You'll be prompt to enter a password for later use in MOK.

###Reboot
`reboot`

##MOK Enrollment

1.  Press anykey to enter MOK within 10 seconds.
2.  Enroll MOK
3.  Continue
4.  Insert the password you just created.
5.  OK

##Check if the Module is Signed
`mokutil --list-enrolled`
