TCP CHINA (Linux 4.7-6.13)
========

`TCP-CHINA` Congestion control algorithm, based on very few modifications
to `TCP-AFRICA`. 

Modifications are simple: Always keep using fast mode of `TCP_AFRICA`

This is yet another demostration of how easily we can increase TCP sending speed
from the server side if you ignore fairness and friendliness.

WARNING: DO NOT USE THIS MODULE! \
It is unfair to other users if your connection is shared!

Moddified to support Linux 4.7+ \
Tested working on 6.6.72 LTS & 6.13.11

Original supports Linux 2.6 - 4.6 \
https://github.com/madeye/tcp_china/

How to build & install on Arch Linux based system:
```
makepkg -f
sudo pacman -U tcp_china-dkms-*.pkg.tar.zst
```

How to build & install, and uninstall on other systems:
```
$ make
# make install
# make uninstall
```

How to use:
```
# Load tcp_china module if not already
sudo modprobe tcp_china

# Make sure it is loaded
lsmod | grep tcp_china

# Set your congestion control to china (does not persist over reboots)
sudo sysctl -w net.ipv4.tcp_congestion_control=china
```