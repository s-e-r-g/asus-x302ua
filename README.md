# Linux setup instructions for Asus-x302ua r4055d 

* Enable_wifi:

<code>sudo echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf</code>

* Enable brightness buttons : handled (icon shown) but brightness doesn't change:

This part enables brightness/wireless hotkey

<pre>
sudo mcedit /etc/default/grub
</pre>

Change
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

<pre>
// TODO: try this one
// GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= acpi_backlight=intel"
</pre>

<pre>
sudo update-grub
sudo reboot
</pre>

and this

<code>
sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf
sudo nano /usr/share/X11/xorg.conf.d/20-intel.conf

Add the following lines to this file:
<pre>
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
</pre>

</code>




Links:
https://ubuntuforums.org/showthread.php?t=2181558
