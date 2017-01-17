> [1. Files & Scripts](https://github.com/ngpfontaine/linux/blob/master/README.md#files--scripts)   
> [2. Applications](https://github.com/ngpfontaine/linux/blob/master/README.md#applications)   
> [3. Command Reference](https://github.com/ngpfontaine/linux/blob/master/README.md#command-reference)   
> [4. Support Links](https://github.com/ngpfontaine/linux/blob/master/README.md#support-links)   

# 1. Files & Scripts      
    
### /home/nic   
    
`.Xmodmap` - natural mouse scrolling  
`.xb` - xboxdrv configuration for 1 xbox 360 controller  
`.move-next-monitor.sh` - send window to other monitor (install ***wdotool*** & ***wmctrl***)   
`.xinput-evoluent.sh` - btn config for evoluent mouse (change ID # per usb slot)
    
### /bin  
    
`xbc` - cmd for launching xboxdrv w/ config file  

# Applications

### INSTALL    
- neofetch (terminal system specs)
- evolution (for gnome calendar)   
- avr-gcc   
- albert (launcher)
- m64py (n64 emulator)
- unetbootin (boot drive creator)
- zsnes (snes emulator)
- rambox (electron chat aggregate)
- indicator-sound-switcher
- kdenlive (video)
- gnome-twitch
- twitch-curses
- livestreamer
- indicator-cpufreq
- tlp
- jupiter
- deluge (torrent)
- sc-controller
- steam-devices
- ranger    
- doom-wad-shareware
- prboom-plus (for doom)
- glances (system monitor)
- volti (audio applet)
- unclutter (hide cursor)
    
    
### CHECK-OUT    
- peek (gif screen recording)
- polybar (system status-bar)
- powerline (terminal status-bar)
- cwiid (wiimote)
- wiican (wiimote)
- tilda
- ksuperkey

# Command Reference

### GRAPHICS DRIVERS    

Check nvidia drivers/packages installed   
`pacman -Ss nvidia | grep installed`    
    
Check OpenGL status   
`glxinfo | grep OpenGL`      

set nvidia as default   
`mhwd-gpu --setgl nvidia`   

nvidia version & info   
`nvidia-smi`   

### GRUB    

`update-grub`   
`grub-mkconfig`   

### DRIVES    

to list all drives' UUIDS   
`sudo blkid`   

`fdisk -l`   
`lsblk`   

mount drive to `/mnt` dir   
`mount /dev/sda1 /mnt/`   
`umount /dev/sda1`   

### APPLICATIONS    

start xampp   
`sudo /opt/lampp/lampp start`   

tor   
cd into the tor dl directory, then run the next command   
`./start-tor-browser.desktop`   

### SSH & SERVER    

create local, public ssh key    
`ssh-keygen -t rsa`   

add to auth keys on server   
`cat ~/.ssh/id_rsa.pub | ssh [user]@[IP address] "cat >> ~/.ssh/authorized_keys"`   

print local ssh key   
`cat ~/.ssh/id_rsa.pub`   

check access log   
`sudo tail -100 /var/log/apache2/access.log`   

check error log   
`sudo tail -100 /var/log/apache2/error.log`    

### INPUT    

xinputs   
`xinput list`   

list props for xinput id=8   
`xinput list-props 8`    

xboxdrv   
`xboxdrv...`    

### AUDIO    

mute pulseaudio output   
`/usr/bin/pulseaudio-ctl mute`      

mute pulseaudio mic   
`/usr/bin/pulseaudio-ctl mute-input`   

change / mute toggle audio   
`amixer -D pulse sset Master 5%+`   

### UBUNTU    

change timezone   
`sudo dpkg-reconfigure tzdata`   

online acct. integration (xubuntu)
`sudo apt install gnome-control-center`   
`env XDG_CURRENT_DESKTOP=GNOME gnome-control-center`   

### NETWORK    

find name of local net device   
`ls /sys/class/net`   

### PERMISSIONS    

sudoers, disable sudo auth on script   
`[USER] ALL = NOPASSWD: /usr/bin/[SCRIPT NAME]`   

# Support Links

[SSH Win to Home Linux w/ Putty - Superuser.com](http://superuser.com/questions/603831/how-to-connect-home-computers-linux-from-office-computer-windows-using-putty)   

[Maya 2016 SP6 - Autodesk.com](https://knowledge.autodesk.com/support/maya/downloads/caas/downloads/content/maya-2016-service-pack-6.html)

