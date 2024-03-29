# rtl8812au

## Realtek 8812AU driver version 5.6.4.1

Only supports 8812AU chipset.

Works fine with 5.3-rc7 kernel. Source now builds with no warnings or errors.

** However module is tainted and needs work to make it kosher.
** Version 5.2.20.2 is not tainted and is the preferred version, thus far.

Added (cosmeticly edited) original Realtek_Changelog.txt, this README.md and dkms.conf.

Added device USB IDs, sorted by ID number.
Added regdb files.

Removed LED control, which was added for driver version 5.2.20

### Building

To build and install module manually:
```sh
$ make
$ sudo make install
```

To use dkms install:

```sh
  (as root, or sudo) copy source folder contents to /usr/src/rtl8812au-5.6.4.1
```

```sh
$ sudo dkms add -m rtl8812au -v 5.6.4.1
$ sudo dkms build -m rtl8812au -v 5.6.4.1
$ sudo dkms install -m rtl8812au -v 5.6.4.1
```

To use dkms uninstall and remove:

```sh
$ sudo dkms remove -m rtl8812au -v 5.6.4.1 --all
```

### NetworkManager

As others have noted, people using NetworkManager need to add this stanza to /etc/NetworkManager/NetworkManager.conf

```sh
  [device]
  wifi.scan-rand-mac-address=no
```

### Regdb files

If needed, copy the regulatory database files in regdb/ to /lib/firmware/

```sh
$ sudo cp ./regdb/* /lib/firmware/
```
