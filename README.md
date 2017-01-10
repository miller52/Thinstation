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

1. Execute command for Clean chroot
```
sudo ./setup-chroot -c
```
2. Copy files to Thinstation directory and Add First Line in /ts/etc/prt-get.conf
```
prtdir /usr/ports/contrib
runscripts yes
```
3. Enter to TS (sudo ./setup-chroot)
4. Run the following command:

Install & upgrade Dependency
```
prt-get remove cyrus-sasl
prt-get update $(prt-get quickdep virt-viewer)
```

add line in your file build.conf
```
packages spice-gtk
```

