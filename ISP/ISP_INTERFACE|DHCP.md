#Interfaces

Links the inside networks to the outside networks
```
interface FastEthernet0/0
 ip address 94.65.3.1 255.255.255.0
 ip nat outside
 duplex auto
 speed auto
```
Connects the Webserver/DNS server/FTP Server
```
interface FastEthernet0/1
 ip address 8.8.8.1 255.255.255.0
 ip nat inside
 duplex auto
 speed auto
```
Connects to the PC with DCHP
```
interface FastEthernet1/0
 ip address 94.65.4.1 255.255.255.0
 ip nat inside
 duplex auto
 speed auto
```
Connects 2 Webservers/FTP Server
```
interface FastEthernet1/1
 ip address 94.65.5.1 255.255.255.0
 duplex auto
 speed auto
```

#DHCP
```
 ip dhcp pool DHCP
 network 94.65.4.0 255.255.255.0
 default-router 94.65.4.1
 dns-server 8.8.8.8
```
#Routes
```
ip route 0.0.0.0 0.0.0.0 94.65.5.2 
ip route 192.168.1.0 255.255.255.0 94.65.5.2 
```
```
