# Linux setup instructions for Asus-x302ua r4055d 

_Enable_wifi_:

<code>echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf</code>


_INCOMPLETE: enable brightness buttons : handled (icon shown) but brightness doesn't change:_ 
* sudo gedit /etc/default/grub

* Change
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
    
* sudo update-grub
* sudo reboot




Links:
https://ubuntuforums.org/showthread.php?t=2181558
