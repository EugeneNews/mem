# nvidia section

## Links

- [Discrete card as primary GPU](https://wiki.archlinux.org/index.php/PRIME#Discrete_card_as_primary_GPU) - PRIME is a technology used to manage hybrid graphics found on recent desktops and laptops

- [xconfigoptions - AllowPRIMEDisplayOffloadSink](https://us.download.nvidia.com/XFree86/Linux-x86_64/460.56/README/xconfigoptions.html#AllowPRIMEDisplayOffloadSink) - driver options are supported by the NVIDIA X driver. They may be specified either in the Screen or Device sections of the X config file.

- [RandR](https://us.download.nvidia.com/XFree86/Linux-x86_64/460.56/README/randr14.html) - To use the NVIDIA driver as an RandR 1.4 output source provider, also known as “PRIME”, the X server needs to be configured to use the NVIDIA driver for its primary screen and to use the “modesetting” driver for the other graphics device

- [nvidia-driver DEBIAN](https://packages.debian.org/sid/nvidia-driver)


### current snippets
/etc/X11/xorg.conf.d/10-dual-monitors.conf

```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
#    ModeDebug  true
    Option "AllowNVIDIAGPUScreens"
#    AllowPRIMEDisplayOffloadSink       "true"
EndSection

Section "Device"
    Identifier  "nvidia"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
EndSection

#Section "Monitor"
#        Identifier      "Monitor0"
#EndSection

Section "Screen"
    Identifier "nvidia"
#    Monitor    "Monitor0"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration"
EndSection

Section "Device"
    Identifier  "intel"
    Driver      "modesetting"
#    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

#Section "Monitor"
#        Identifier      "Monitor1"
#EndSection

Section "Screen"
    Identifier "intel"
 #   Monitor    "Monitor1"
    Device "intel"
EndSection
```



