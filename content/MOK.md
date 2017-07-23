Title: Managing Signed Keys with Machine Owner Key
Date: 2017-07-23 21:46:00
Category: Fedora
Tags: Fedora, Yee, Secure Boot, MOK

[TOC]

##Introduction

With MOK we can sign, manage, and delete keys for installed kernel modules.

##Usage

###Enrolling a key
The guide can be found [here](https://superdanby.github.io/Blog/signing-kernel-modules-for-secure-boot.html).

###List all the enrolled keys:
    `mokutil -l`

###Deleting a key
First, you have to export the keys: `mokutil --export`

Delete the key: `mokutil -d `*TheFile* \t E.g. `mokutil -d MOK-0001.der`
