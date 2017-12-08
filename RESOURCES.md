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
- ncdu (ncurses disk usage)
- gpick (colorpicker)   
- mc (terminal file browser w/ ftp)   
- rofi (launcher)   
- rtv (reddit terminal viewer)
- ffado (firewire audio devices)
- bookworm (e-book reader)
    
### CHECK-OUT    
- peek (gif screen recording)
- polybar (system status-bar)
- powerline (terminal status-bar)
- cwiid (wiimote)
- wiican (wiimote)
- tilda
- ksuperkey
- dunst (desktop notifications)
- kde connect (connect devices & control)
- slash (slack terminal)
- master pdf editor   

### GNOME EXTENSIONS
- background logo
- dash to dock
- hide activities button
- straight top bar

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

ffmpeg batch convert
`for i in *.avi; do ffmpeg -i "$i" "${i%.avi}.mov"; done`    

xclip (clipboard)
`xclip -sel c < [file]`   


### NODE

won't install
`rm -rf node_modules && npm cache clean && npm install`   

symbolic link for nodejs & node
`ls -s /usr/bin/nodejs/usr/bin/node`   

### GIT   

overwrite local
`git reset --hard origin/master`   

add remote repo url to local proj
`git remote add origin [url]`   

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

signing fails when adding key b/c ssh-agent already running
`ssh-add`   

### NEW WEBSITE   

add nameservers to registrar   

create NS, A, & CNAME records at host  
- A example.com > ip.add.re.ss
- NS example.com > ns1.host.com.
- CNAME www.example.com > example.com   

make dir for it, & grant ownership
`sudo mkdir -p /var/www/example.com/public_html`
`sudo chown -R $USER:$USER /var/www/example.com/public_html`

copy vhost, then edit server name, doc root, & alias within file
`sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/example.com.conf`   

add redirect to conf file
`ServerName www.example.com`
`ServerAlias example.com`
`Redirect permanent / https://example.com/`   

copy and edit conf-le-ssl... file   

enable vhost file
`sudo a2ensite example.com.conf`   

restart apache
`sudo service apache2 restart`   

ssl
`certbot-auto --apache -d example.com -d www.example.com -d other.com [...]`   

letsencrypt w/ webroots
`./letsencrypt-auto certonly --webroot -w 
/var/www/domain.com/public_html -d www.domain.com -d domain.com -w 
/var/www/mysite.net/public_html -d www.mysite.net -d mysite.net -w 
/var/www/nicepage.org/public_html -d www.nicepage.org -d nicepage.org`   

### RSYNC   

ignorelist
`wget https://raw.githubusercontent.com/rubo77/rsync-homedir-excludes/master/rsync-homedir-excludes.txt -O /var/tmp/ignorelist`   

backup
`rsync -aP --exclude-from=/var/tmp/ignorelist /home/$USER/ /media/$USER/<drive>/<dir>/`      


### INPUT    

xinputs   
`xinput list`   

list props for xinput id=8   
`xinput list-props 8`    

xboxdrv, hotplug 1 controller
`sudo xboxdrv -c /home/nic/.xb01 -D`    

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

### ARCH

error: failed to commit transaction (invalid or corrupted package)   
```sudo pacman-key --refresh-keys
sudo pacman -S archlinux-keyring
sudo pacman -Syu
```   

### NETWORK    

find name of local net device   
`ls /sys/class/net`   

### PERMISSIONS    

sudoers, disable sudo auth on script   
`[USER] ALL = NOPASSWD: /usr/bin/[SCRIPT NAME]`   

### ETC   

change default home dir names
`vim ~/.config/user-dirs.dirs`   

private internet access installer
`wget https://www.privateinternetaccess.com/installer/pia-nm.sh`   

fix multi-monitor workspaces on gnome
`gsettings set org.gnome.shell.overrides workspaces-only-on-primary false`   

# Support Links

[SSH Win to Home Linux w/ Putty - Superuser.com](http://superuser.com/questions/603831/how-to-connect-home-computers-linux-from-office-computer-windows-using-putty)   

[Maya 2016 SP6 - Autodesk.com](https://knowledge.autodesk.com/support/maya/downloads/caas/downloads/content/maya-2016-service-pack-6.html)

[yktools - touchpad toggle](https://github.com/yktoo/yktools/blob/master/touchpad-toggle)  

[Private Git Server - DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-git-server-on-a-vps)    

[Manage Dotfiles on github - smalley](http://blog.smalleycreative.com/tutorials/using-git-and-github-to-manage-your-dotfiles/)  

[Encrypt home folder Ubuntu - Howtogeek](http:/www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/)
