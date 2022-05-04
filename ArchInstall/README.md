## Just how to Install Arch

## how to connect to a wifi network in archiso

root@archiso ~ # iwctl

[iwd]# device list

[iwd]# station wlan0 scan

[iwd]# station wlan0 get-networks

[iwd]# station wlan0 connect iballbaton

passphrase: ***********

## Now check if you are connected to the internet

root@archiso# ping google.com
