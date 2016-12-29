# Thinstation port and dependency for Spice-Gtk 0.33

Status: ***Not working***



```
configure:

        Spice-Gtk 0.33
        ==============

        prefix:                   /usr
        c compiler:               gcc
        Target:                   Unix

        Gtk:                      no
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
2. Enter to TS (sudo ./setup-chroot)
3. Run the following command:

Enables if not the user maintained contrib collection in /usr/ports/contrib
```
sed -i 's|#prtdir /usr/ports/contrib|prtdir /usr/ports/contrib|' /ts/etc/prt-get.conf
```
Install & upgrade Dependency
```
prt-get remove cyrus-sasl
prt-get depinst libsasl2 --config-prepend="prtdir /usr/ports/contrib"
prt-get depinst libcacard --config-prepend="prtdir /usr/ports/contrib"
prt-get depinst gstreamer-1.0 --config-prepend="prtdir /usr/ports/contrib"
prt-get depinst gstreamer-plugins-base-1.0 --config-prepend="prtdir /usr/ports/contrib"
prt-get depinst gstreamer-plugins-libav-1.0 --config-prepend="prtdir /usr/ports/contrib"
prt-get depinst gstreamer-plugins-good-1.0 --config-prepend="prtdir /usr/ports/contrib"
prt-get depinst gstreamer-plugins-bad-1.0 --config-prepend="prtdir /usr/ports/contrib"
prt-get depinst gstreamer-plugins-ugly-1.0 --config-prepend="prtdir /usr/ports/contrib"
prt-get update spice-protocol --config-prepend="prtdir /usr/ports/contrib"
prt-get update spice --config-prepend="prtdir /usr/ports/contrib"
prt-get update libpcre --config-prepend="prtdir /usr/ports/contrib"
prt-get update glib --config-prepend="prtdir /usr/ports/contrib"
prt-get depinst orc --config-prepend="prtdir /usr/ports/contrib"
prt-get install libusb
prt-get depinst libusbredir --config-prepend="prtdir /usr/ports/contrib"
prt-get update libsoup --config-prepend="prtdir /usr/ports/contrib"
prt-get depinst libphodav --config-prepend="prtdir /usr/ports/contrib"
prt-get update spice-gtk --config-prepend="prtdir /usr/ports/contrib"
```

add line in your file build.conf
```
packages spice
```

