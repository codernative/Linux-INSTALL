# To improve the fonts in Arch 


First need to add some additional fonts.  
```
sudo pacman -S ttf-bitstream-vera ttf-inconsolata ttf-ubuntu-font-family ttf-dejavu ttf-freefont ttf-linux-libertine ttf-liberation
```
yay -S ttf-ms-fonts ttf-vista-fonts ttf-monaco ttf-qurancomplex-fonts 




Next we will disable bitmat fonts, which are used as a fallback.  

sudo ln -s /etc/fonts/conf.avail/70-no-bitmaps.conf /etc/fonts/conf.d

Now we need to add the Infinality repo to our pacman.conf file.  To do this, open the file with gedit (or whatever text editor your using):

sudo gedit /etc/pacman.conf

Add the following to your pacman.conf to use the infinality repo:

[infinality-bundle]
SigLevel = Never
Server = http://bohoomil.com/repo/$arch

[infinality-bundle-multilib]
SigLevel = Never
Server = http://bohoomil.com/repo/multilib/$arch

[infinality-bundle-fonts]
SigLevel = Never
Server = http://bohoomil.com/repo/fonts

Then uncomment the multilib on pacman configuration to download and install 32 bit package on 64 bit systems
[multilib] 
Include = /etc/pacman.d/mirrorlist

Install the bundle:

sudo pacman -Syy infinality-bundle infinality-bundle-multilib

Finally, reboot your system.  For more insite on using Infinality fonts visit:

https://wiki.archlinux.org/index.php/...

http://www.infinality.net/blog/infina...
