# Linux setup instructions for Asus-x302ua r4055d 

## HW configuration
* CPU : i5 6200U
* RAM : 8GB DDR3
* GFX : Intel 
* WIFI: Atheros ???? 

## Fixes
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


* Setting DPI

Not so good solution with DPI:

https://wbk.one/article/8/dpi-scaling-on-linux-mint

DPI Scaling on Linux Mint

I have a Surface Pro 2 which has a relatively dense, 10-inch 1080p screen. It hurts my eyes to look at individual UI elements and text without dpi scaling. On Windows, everything is scaled up by 150% by default.

I wanted to use Linux Mint on VirtualBox for development but I couldn't find any articles on the internet on how to get the elements to scale up properly. After some trial-and-error, this is how I achieved 150% dpi scaling that is good enough.

    Go to Preference -> General, then select User interface scaling to be Double. This doubles everything in size. This works for other high density displays like MacBook Pro retina but many things looked too big for the screen of Surface Pro 2.
    Go to Preference -> Fonts, then set text scaling factor to 0.7. This leaves UI elements to be double the size but makes text smaller. Since the text size was doubled then multiplied by 0.7, it ends up being 140% of the original size, which is close enough to the desired level of 150%.
    Log out and back in to finish applying the change.

 


##Links:

* https://ubuntuforums.org/showthread.php?t=2181558
* http://askubuntu.com/questions/471847/brightness-fn-key-shortcut-doesnt-work-on-asus-laptop/841903
* https://wbk.one/article/8/dpi-scaling-on-linux-mint
