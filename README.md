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

Store fixsamba to /jffs on the router
```
chmod 755 /jffs/fixsamba
```

```
nvram set script_usbmount="/jffs/fixsamba"
nvram commit

```

Upon either rebooting, or disconnecting / reconnecting the USB drive, the script will execute, kill all existing smbd processes, copy the custom configuration file into place, and restart smbd.
