# Thinstation port and dependency for Spice-Gtk 0.33

Status: ***Not working***



```
configure:

        Spice-Gtk 0.33
        ==============

        prefix:                   /usr
        c compiler:               gcc
        Target:                   Unix

        Gtk:                      gtk3
        Coroutine:                ucontext
        PulseAudio:               yes
        GStreamer Audio:          yes
        GStreamer Video:          yes
        SASL support:             yes
        Smartcard support:        yes
        USB redirection support:  yes with libusb hotplug
        DBus:                     yes
        WebDAV support:           yes
        LZ4 support:              yes
```


Instruction:

1. Copy files to Thinstation directory
1.1 Add first line in /ts/etc/prt-get.conf
```
prtdir /usr/ports/contrib
runscripts yes
```
2. Enter to TS (sudo ./setup-chroot)
3. Run the following command:


Clean chroot
```
clean_chroot
```

Install & upgrade Dependency
```
prt-get remove cyrus-sasl
prt-get update $(prt-get quickdep virt-viewer)
```

add line in your file build.conf
```
packages spice-gtk
```

