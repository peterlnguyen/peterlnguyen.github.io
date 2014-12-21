---
layout: post
title: Arch Backup
permalink: arch-backup
tags: linux, arch
---


<div class="message">
  Backing up Arch linux onto an external drive
</div>

### Attaching your device

List your devices:  
`sudo udisks -l`  

Mount selected device  
`sudo udisks -mount /dev/sdc3`  

### Create backup

As root, run:  
```
rsync -aAXv /* /path/to/backup/folder 
               --exclude={/dev/*,/proc/*,/sys/*,/tmp/*,/run/*,/mnt/*,/media/*,/lost+found}  
```

Or create a file bin/backup according to the [Arch wiki](https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync).  

Make it executable:  
```
chmod +x bin/backup  
```

Run file and choose external as target:  
```
sudo bin/backup /media/LINUX/  
```

### Unmount

Finally, don't forget to unmount:  
```
sudo umount /path/to/device  
```

And voila, there's your entire backup process!


-----
