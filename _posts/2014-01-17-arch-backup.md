Attach device, and list disks with:  
`sudo udisks -l`  

Mount selected device with  
`sudo udisks -mount /dev/sdc3`  

As root, run:  
```# rsync -aAXv /* /path/to/backup/folder --exclude={/dev/*,/proc/*,/sys/*,/tmp/*,/run/*,/mnt/*,/media/*,/lost+found}```  

Or create a file bin/backup: https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync  

Make it executable:  
`chmod +x bin/backup`  

Run file and choose external as target:  
`sudo bin/backup /media/LINUX/`  

Unmount with: 
`sudo umount /path/to/device`  


