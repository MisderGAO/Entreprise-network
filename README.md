# Entreprise-network
Functionality：

1.	Vlans are configured to separate different department.
2.	HSRP + PV-STP are deployed in local exchange to realize the gateway redundancy and load balancing.
3.	Ethernet-channel is used between 2 layer-3 switch in order to enhance stability and speed of packet exchange.
4.	Data center (DC) is connected to core router through PIX FW, composed by servers of DHCP, DNS, NTP, RADIUS and LDAP.
5.	ASA is the FW of the whole enterprise, Policies, VPNs , NAT and AAA servers (directed to DC) are defined here.
6.	WEB SERVER is placed in DMZ 
7.	Enterprise has exits out to two different ISPs; two exits are BGP connected to the enterprise.
8.	ISP routers are bridged via GNS3 NAT node to the laptop Ethernet Card in order to simulate the connection to the internet.
9.	Two different Site to site VPNs are deployed between headquarter and branch. One is MPLS VPN (guaranteed by ISP), another is IPSEC VPN     (guaranteed by USERS).

Assignment of IP address:

Vlan 10: 192.168.1.0/24 192.168.1.254
Vlan 20: 192.168.2.0/24 192.168.2.254
Vlan 30: 192.168.3.0/24 192.168.3.254
Vlan 40: 192.168.4.0/24 192.168.4.254
DC: DHCP, NTP and DNS server 172.16.2.100/24
LDAP and RADIUS server 172.16.2.101/24
DMZ: web server 172.16.1.1 (public: 200.1.1.5)
ISP1:200.100.1.0/30
ISP2: 200.100.2.0/30
Branch: 192.168.10.0/24 192.168.10.254

SECURITY POLICY: 

ALL vlan members can access Internet;
Vlan 10 is allowed to commmunicate with the branch site via VPN;
DMZ can be accessed by Internet in the way of http and icmp.
HTTP, FTP, TELNET are available for Branch to access DMZ through VPN.
VPN access needs to be authenticated by LDAP server.
Telnet to Firewall needs to be authenticated by RADIUS server.
ISP1 is more preferable to ISP2 when access to internet is initiated.
