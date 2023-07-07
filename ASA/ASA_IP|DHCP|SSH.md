#INTERFACE CONFIG

Interface that connects the inside networks to the outside networks.
```
interface GigabitEthernet1/1
 nameif outside
 security-level 0
 ip address 94.65.3.2 255.255.255.0
```
Link between the webserver and ASA
```
interface GigabitEthernet1/2
 nameif dmz
 security-level 0
 ip address 192.168.1.1 255.255.255.0
```
Link between dhcp endpoints and ASA
```
interface GigabitEthernet1/3
 nameif inside
 security-level 0
 ip address 172.16.1.1 255.255.255.0
```

#DHCP CONFIG

```
dhcpd address 172.16.1.10-172.16.1.20 inside
dhcpd dns 8.8.8.8 interface inside
dhcpd enable inside
```
#Routes
```
route outside 0.0.0.0 0.0.0.0 94.65.3.1 1
route outside 8.8.8.8 255.255.255.255 94.65.3.1 1
```

#SSH

```
ssh 172.16.1.0 255.255.255.0 inside
```
