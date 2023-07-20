# ASA Firewall

The ASA Firewall exercise on Packet Tracer focused on deepening knowledge in firewall concepts. The network topology featured an ASA connected to an ISP, with two private networks managed by the ASA. NAT was used for external communication, and access control rules were implemented on the firewall.

The ASA's private network consisted of three PCs that received IP addresses through DHCP from the ASA. The ASA's second private network hosted a simple server providing HTTP/HTTPS web services and an FTP server. The ASA's public interface served as the only outside NAT interface, connected to the ISP.

On the ISP side, there were three private networks. One network had a single PC using DHCP from the ISP. Another network featured a simple server offering HTTP/HTTPS services and a DNS server used by all PCs in the topology. The DNS server exclusively translated the server IPs connected to the ISP. The last private network contained two servers, one for serving a web server and the other for FTP services.

The objective was to configure the ASA's firewall to enhance network security. Access control rules were set up to allow only one network from the outside to access the ASA's web server, ensuring restricted and controlled access. Additionally, the ASA's DHCP PCs were permitted to connect to the servers outside the ASA, enabling specific and authorized communication.

This exercise demonstrated practical application of firewall rules and NAT configurations on the ASA, solidifying understanding and skills in firewall management and network security, while also showcasing the ISP side with its server services and DNS translation for connected servers.
