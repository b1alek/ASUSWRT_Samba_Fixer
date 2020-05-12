ASUSWRT_Samba_restart_after_boot
=============

Kill and restart the smbd daemon. Designed to be run at boot time, on a router with an attached USB storage drive.


Out of the box, the Asus RT-AC87 router has some handy, but limited, file and media sharing capabilities. Connect a USB hard drive to one of its USB ports, and the router can share data from that drive with anyone on your network.

Requirements:
=============

* Runs on an Asus wireless router using ASUSWRT firmware. This is known to work on the Asus RT-AC87U; it likely works on most other RT-XXXXX models running version 3.0.0.4 or newer. 
* This only works if a USB drive is attached

Usage: 
=============

Downloadn, make exacutable and commit changes to router.
```
Using an SSH client to login to your router, then copy and paste the following command:

/usr/sbin/wget --tries=3 --timeout=3 --no-check-certificate -O "/jffs/smbd_restart.sh" "https://raw.githubusercontent.com/b1alek/ASUSWRT_Samba_Restart_After_Boot/master/smbd_restart.sh" && chmod 755 /jffs/smbd_restart.sh && nvram set script_usbmount="/jffs/smbd_restart.sh" && nvram commit
```

Upon either rebooting, or disconnecting / reconnecting the USB drive, the script will execute, kill all existing smbd processes, copy the custom configuration file into place, and restart smbd.
