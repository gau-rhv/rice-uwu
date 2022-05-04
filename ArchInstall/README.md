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

Pinging google.com [2404:6800:4007:808::200e] with 32 bytes of data:

Reply from 2404:6800:4007:808::200e: time=70ms

Reply from 2404:6800:4007:808::200e: time=65ms

Reply from 2404:6800:4007:808::200e: time=60ms

Reply from 2404:6800:4007:808::200e: time=58ms

Ping statistics for 2404:6800:4007:808::200e: 

Packets: Sent = 4, Received = 4, 

Lost = 0 (0% loss), Approximate round trip times in milli-seconds: Minimum = 58ms

Maximum = 70ms, Average = 63ms

![Screenshot (25)](https://user-images.githubusercontent.com/102450738/164955813-d23ae0f5-43c9-4c78-a20f-c9382cf06f63.png)

## Check the partitions
