***GRAPHICS DRIVERS***    

// Check nvidia drivers/packages installed   
`pacman -Ss nvidia | grep installed`    

// Check OpenGL status   
`glxinfo | grep OpenGL`      

// set nvidia as default   
`mhwd-gpu --setgl nvidia`   

// nvidia version   
nvidia-smi   

***GRUB***    

`update-grub`   
`grub-mkconfig`   

***DRIVES***    

// to list all drives' UUIDS   
`sudo blkid`   

fdisk -l   
lsblk   

// mount drive to `/mnt` dir   
mount /dev/sda1 /mnt/   
umount /dev/sda1   

***APPLICATIONS***    

// start xampp   
`sudo /opt/lampp/lampp start`   

// tor   
// cd into the tor dl directory, then run the next command   
`./start-tor-browser.desktop`   

***SSH & SERVER***    

// print local ssh key   
`cat ~/.ssh/id_rsa.pub`   

// check logs   
`sudo tail -100 /var/log/apache2/access.log`   
`error.log`   

// ADD PUBLIC SSH KEY TO SERVER   
ssh-keygen -t rsa   
cat ~/.ssh/id_rsa.pub | ssh [user]@[IP address] "cat >> ~/.ssh/authorized_keys"   

***INPUT***    

// xinput properties   
`xinput list`   
`xinput list-props 8`    

// Xbox controller   
- xboxdrv   
- qjoypad   

***AUDIO***    

// mute pulseaudio output   
/usr/bin/pulseaudio-ctl mute      

// mute pulseaudio mic   
/usr/bin/pulseaudio-ctl mute-input   

// change / mute toggle audio   
amixer -D pulse sset Master 5%+   

***UBUNTU***    

// CHANGE TIMEZONE UBUNTU   
sudo dpkg-reconfigure tzdata   

// ONLINE ACCTS ON XUBUNTU   
install gnome-control-center   
env XDG_CURRENT_DESKTOP=GNOME gnome-control-center   

***NETWORK***    

// FIND NAME OF LOCAL NET DEVICE   
ls /sys/class/net   

***PERMISSIONS***    

// SUDOERS, DISABLE SUDO AUTH ON SCRIPT   
YOURNAME ALL = NOPASSWD: /usr/bin/apache2ctl   
