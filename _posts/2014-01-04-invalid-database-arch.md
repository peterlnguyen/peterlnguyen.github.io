---
layout: post
title: Invalid Pacman Database - Arch
permalink: invalid-database-arch-pacman
tags: linux, arch, pacman
---


<div class="message">
  Solving pacman database errors with Arch linux
</div>

### Update Errors
Since Arch is a rolling-release distro, it requires regular update and maintenance.  I've gotten away with not updating for a pretty long time, but eventually I just had to sit down, upgrade, and untangle the dependencies and conflicts to upgrade a library I needed.  


This is what happened:  

```
sudo pacman -Syu
error: GPGME error: No data
:: Synchronizing package databases...
  xorg113                               10.4 KiB   125K/s 00:00 [##################################] 100%
  xorg113.sig                           10.4 KiB  0.00B/s 00:00 [##################################] 100%
error: GPGME error: No data
error: failed to update xorg113 (invalid or corrupted database (PGP signature))
  core is up to date
  extra                               1441.1 KiB   975K/s 00:01 [##################################] 100%
  community                              2.0 MiB  1127K/s 00:02 [##################################] 100%
  multilib                             109.7 KiB   245K/s 00:00 [######################
error: database 'xorg113' is not valid (invalid or corrupted database (PGP signature))
```

### Resign Keys

I google around a bit, and someone suggested I re-sign:

```
sudo pacman-key --keyserver pgp.mit.edu --recv-keys 0xabed422d653c3094
sudo pacman-key --lsign-key 0xabed422d653c3094
```

### Not requiring digitally signed packages

This seemed to solve the issue for a few, but not most.  
Changing the SigLevel from "Required DatabaseOption" to "Never" did the trick for me:

###### /etc/pacman.d/conf
```
#SigLevel    = Required DatabaseOptional
SigLevel    = Never
```

### Further reading:  
[Disable Signature Checking](https://wiki.archlinux.org/index.php/Pacman-key#Disabling_signature_checking)  
[Unrecognized Archive Format](https://bbs.archlinux.org/viewtopic.php?id=13531k0)  





