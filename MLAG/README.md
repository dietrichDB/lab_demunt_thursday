LAB OVERVIEW: 4-Switch MLAG-Based Data Center Fabric

Topology

2 Leaf switches (LEAF1 and LEAF2) in an MLAG pair

2 Spine switches (SPINE1 and SPINE2) for upstream connectivity

Server(s) connected to the MLAG pair for active-active connectivity


1\. Build your Containerlab Topology File first! (use the 3CLAB as an example but you need to modify it!!!)

2\. Basic interface IP and VLAN config

MLAG using peer link and keepalive

Active-active LAG to downstream hosts

SPINEs use Layer 3 underlay or static routes (simplified)

BASE ASSUMPTIONS

ElementValue

MLAG Domain10

Peer LinkEthernet3

KeepaliveManagement1

Server PortsEthernet1

SPINE LinksEthernet5 & Ethernet6

VLAN ID10

VLAN NameServer\_VLAN

SVI IP10.0.10.1/24 (VARP)

Host IPsStatic or via DHCP

3\. LAB CONFIGS

\*\*\* SPINE1 & SPINE2 \*\*\*

!

hostname SPINE1

interface Ethernet1

no switchport

ip address 192.168.1.1/31

!

interface Ethernet2

no switchport

ip address 192.168.1.5/31

!

ip routing

!

(Repeat similarly on SPINE2 with IPs 192.168.1.3/31 and 192.168.1.7/31)

\*\*\* LEAF1 CONFIG \*\*\*

hostname LEAF1

!

interface Management1

ip address 10.0.0.1/24

!

interface Ethernet3

channel-group 100 mode active

!

interface Ethernet5

no switchport

ip address 192.168.1.0/31

!

interface Ethernet6

no switchport

ip address 192.168.1.4/31

!

interface Port-Channel100

switchport

switchport mode trunk

!

interface Ethernet1

channel-group 1 mode active

!

interface Port-Channel1

switchport

switchport access vlan 10

!

vlan 10

name Server\_VLAN

!

interface Vlan10

ip address virtual 10.0.10.1/24

!

mlag configuration

domain-id 10

local-interface Vlan4094

peer-address 10.0.0.2

peer-link Port-Channel100

!

\*\*\* LEAF2 CONFIG \*\*\*

hostname LEAF2

!

interface Management1

ip address 10.0.0.2/24

!

interface Ethernet3

channel-group 100 mode active

!

interface Ethernet5

no switchport

ip address 192.168.1.2/31

!

interface Ethernet6

no switchport

ip address 192.168.1.6/31

!

interface Port-Channel100

switchport

switchport mode trunk

!

interface Ethernet1

channel-group 1 mode active

!

interface Port-Channel1

switchport

switchport access vlan 10

!

vlan 10

name Server\_VLAN

!

interface Vlan10

ip address virtual 10.0.10.1/24

!

mlag configuration

domain-id 10

local-interface Vlan4094

peer-address 10.0.0.1

peer-link Port-Channel100

!
