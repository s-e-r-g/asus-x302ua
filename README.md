# Linux setup instructions for Asus-x302ua r4055d 

* Enable_wifi:

<code>sudo echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf</code>

* Enable brightness & air buttons:

<pre>
sudo mcedit /etc/default/grub

Change
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

// TODO: try this one
// GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= acpi_backlight=intel"

sudo update-grub
sudo reboot
</pre>

and this

<pre>
sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf
sudo nano /usr/share/X11/xorg.conf.d/20-intel.conf

Add the following lines to this file:

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
</pre>





Links:

https://ubuntuforums.org/showthread.php?t=2181558

http://askubuntu.com/questions/471847/brightness-fn-key-shortcut-doesnt-work-on-asus-laptop/841903
