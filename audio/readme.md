# Audio section

## Links

- [PulseAudio](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting) - PulseAudio/Troubleshooting.

- [Modules](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#module-switch-on-port-available) - PulseAudio/Modules description.

- [ubuntu pulseaudio](https://itectec.com/ubuntu/ubuntu-pulseaudio-not-detecting-bluetooth-headset-automatically/) - Pulseaudio not detecting bluetooth headset automatically.


## How to disable nvidia hdmi audio?

- [archlinux](https://bbs.archlinux.org/viewtopic.php?id=253258) - several advices.


`/etc/pulse/default.pa`

    load-module module-switch-on-port-available


`/etc/modprobe.d/blacklist.conf` - даёт сбои для основной карточки

    install snd_hda_codec_hdmi /usr/bin/true

### systemd подход

`/etc/systemd/system/my-hdmi-remove.service`

    [Unit]
    Description = Remove HDMI module on boot

    [Service]
    ExecStart = rmmod -f snd_hda_codec_hdmi

    [Install]
    WantedBy = multi-user.target

_команды для установки_

        systemd-analyze verify my-hdmi-remove.service
        systemctl enable my-hdmi-remove.service
        systemctl cat sys-fs-fuse-connections.mount


## disable HSP/HFP bluetooth profile

`/etc/bluetooth/audio.conf` 

    [General]
    Disable=Headset

`/etc/pulse/default.pa` and add `auto_switch=false` like this)

    ifexists module-bluetooth-policy.so
    load-module module-bluetooth-policy auto_switch=false  # <---- !
    .endif


- [Auto switch to A2DP bluetooth device when connected in Ubuntu](https://sandalov.org/blog/2146/) - ещё вариант.