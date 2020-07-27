# re101

https://malwareunicorn.org/workshops/re101.html#2

In order to make your boxes/VMs communicate on the same "Internal Network" [ **re101net** ], 
make sure to add a new `dhcpserver` using `VBoxManage`

## Host on Linux/Mac
```
VBoxManage dhcpserver add --netname re101net --server-ip 10.10.10.1 --netmask 255.255.255.0 --lower-ip 10.10.10.111 --upper-ip 10.10.10.112 --enable 
```

## Host on Windows
```
"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" dhcpserver add --netname re101net --server-ip 10.10.10.1 --netmask 255.255.255.0 --lower-ip 10.10.10.111 --upper-ip 10.10.10.112 --enable 
```

## Modify
```
VBoxManage dhcpserver modify --network re101net --server-ip 10.10.10.1 --netmask 255.255.255.0 --lower-ip 10.10.10.111 --upper-ip 10.10.10.112 --enable 
```

## Check success/failure
- ` "C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" dhcpserver list `
- ` VBoxManage dhcpserver list `

In the Sniffer box:
```
/etc/init.d/inetsim start

ps -ef | grep inetsim

ping 10.10.10.111
ping 10.10.10.112
```
