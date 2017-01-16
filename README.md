# Linux setup instructions for Asus-x302ua r4055d 

* Enable_wifi:

<code>sudo echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf</code>

* Enable brightness buttons : handled (icon shown) but brightness doesn't change:

This part enables brightness/wireless hotkey

<code>
sudo mcedit /etc/default/grub

Change
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

# TODO: try this one
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= acpi_backlight=intel"


sudo update-grub
sudo reboot
</code>

and this

<code>
sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf
sudo nano /usr/share/X11/xorg.conf.d/20-intel.conf


Add the following lines to this file:

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection

</code>




Links:
https://ubuntuforums.org/showthread.php?t=2181558
