# Linux for asus-x302ua setup instructions

Enable brightness buttons:

* sudo gedit /etc/default/grub

* Change
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
    
* sudo update-grub
* sudo reboot
