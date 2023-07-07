# OBJECTS

When traffic flows from the server into the dmz interface to the outside network, the ASA will perform NAT translation, replacing the source IP address of the traffic with 94.65.3.2. 
This allows the server to communicate with external networks using the public IP address.
```
object network inside-server
 host 192.168.1.2
 nat (dmz,outside) static 94.65.3.2
```
# ACCESS-LISTS

This ACL permits UDP DNS (Domain Name System) traffic from the server with IP 192.168.1.2 in the DMZ to the DNS server at IP 8.8.8.8. 
This allows the server to perform DNS lookups.
```
access-list dmz_access_out_dns extended permit udp host 192.168.1.2 host 8.8.8.8 eq domain
```
This ACL permits ICMP (Internet Control Message Protocol) traffic from any source to any destination in the DMZ. 
ICMP is used for various network diagnostic purposes, such as ping requests and replies.
```
access-list dmz_access_out_dns extended permit icmp any any
```
This ACL permits TCP traffic from any source to the server with the object name "inside-server" on port 80 (HTTP).
It allows external clients to access the web server hosted on the inside network.
```
access-list outside_access_in extended permit tcp any object inside-server eq www
```
This ACL permits TCP traffic from any source to the server with the object name "inside-server" on port 443 (HTTPS).
It allows external clients to access the secure web server hosted on theinside network.
```
access-list outside_access_in extended permit tcp any object inside-server eq 443
```
This ACL permits TCP traffic from any source to the server with the object name "inside-server" on port 21 (FTP). 
It allows external clients to establish FTP connections with the FTP server hosted on the inside network.
```
access-list outside_access_in extended permit tcp any object inside-server eq ftp
```
This ACL permits UDP DNS traffic from the DNS server at IP 8.8.8.8 to the server with IP 192.168.1.2.
It allows DNS responses to reach the server.
```
access-list outside_access_in extended permit udp host 8.8.8.8 host 192.168.1.2 eq domain
```
This ACL permits UDP DNS traffic from the DNS server at IP 8.8.8.8 to the network 172.16.1.0/24.
It allows DNS responses to reach the network.
```
access-list outside_access_in extended permit udp host 8.8.8.8 172.16.1.0 255.255.255.0 eq domain
```
This ACL permits ICMP traffic from any source to the server with the object name "inside-server".
It allows external clients to ping the server.
```
access-list outside_access_in extended permit icmp any object inside-server
```
This ACL permits UDP DNS traffic from the DNS server at IP 8.8.8.8 to any destination IP on port 53 (DNS).
It allows DNS responses to reach any internal DNS client.
```
access-list outside_access_in extended permit udp host 8.8.8.8 any eq domain
```
This ACL permits TCP traffic from any source to any destination on ports greater than 1000.
It allows incoming TCP connections to non-privileged ports.
```
access-list outside_access_in extended permit tcp any any gt 1000
```
This ACL permits UDP traffic from any source to any destination on ports greater than 1000.
It allows incoming UDP connections to non-privileged ports.
```
access-list outside_access_in extended permit udp any any gt 1000
```
# ACCESS-GROUPS / SSH

This line applies the access group named "dmz_access_out_dns" to the "dmz" interface. 
The access group is used to control inbound traffic to the interface, allowing or denying specific protocols and port numbers based on the configured ACL rules.
```
access-group dmz_access_out_dns in interface dmz
```
This line applies the access group named "outside_access_in" to the "outside" interface. 
Similar to the previous line, this access group controls inbound traffic to the outside interface using the configured ACL rules.
```
access-group outside_access_in in interface outside
```
This line enables local authentication for SSH access to the ASA's console. 
It specifies that the ASA should use the local username and password database for authenticating SSH connections made to the console.
```
aaa authentication ssh console LOCAL
```
