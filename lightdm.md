# lightdm

For disabling SDDM (KDE Systems) type $: sudo systemctl disable sddm

Start out with opening up your /etc/lightdm/lightdm.conf and this is where most of the modifications will take place.

greeter-session=lightdm-slick-greeter ### CHANGE THIS 

Install what ever theme you want, this is called a greeter in lightdm, and then change the line above. 
After the changes are made you can either reboot or type "sudo systemctl restart lightdm" 
Please Note: This will log you out
