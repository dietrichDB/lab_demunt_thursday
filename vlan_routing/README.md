\*\*\* LAB OVERVIEW: 2-Layer Topology with Inter-VLAN Static Routing \*\*\*

Topology

2 Access switches (ACCESS1, ACCESS2) connected to

1 Core switch (CORE1) that performs inter-VLAN routing

1 Management switch (OPTIONAL: MGMT-SW) for out-of-band access

+-------------+

| CORE1 | ← Inter-VLAN routing happens here (SVIs)

+-------------+

| |

| |

+---------+ +---------+

| ACCESS1 | | ACCESS2 |

+---------+ +---------+

| |

\[Host A\] \[Host B\]

VLAN 10 VLAN 20

IP Addressing Plan

VLANSubnetVLAN NameSVI IP (CORE1)Hosts IP Example

10192.168.10.0/24Users192.168.10.1192.168.10.10 (A)

20192.168.20.0/24Servers192.168.20.1192.168.20.20 (B)

\- CONFIGURATIONS

CORE1 (Layer 3 routing switch)

hostname CORE1

!

interface Ethernet1

description Uplink to ACCESS1

switchport

switchport mode trunk

!

interface Ethernet2

description Uplink to ACCESS2

switchport

switchport mode trunk

!

vlan 10

name Users

!

vlan 20

name Servers

!

interface Vlan10

ip address 192.168.10.1/24

!

interface Vlan20

ip address 192.168.20.1/24

!

ip routing

ACCESS1 (Access switch - VLAN 10)

hostname ACCESS1

!

interface Ethernet1

description Host A

switchport access vlan 10

!

interface Ethernet2

description Uplink to CORE1

switchport mode trunk

!

vlan 10

name Users

ACCESS2 (Access switch - VLAN 20)

hostname ACCESS2

!

interface Ethernet1

description Host B

switchport access vlan 20

!

interface Ethernet2

description Uplink to CORE1

switchport mode trunk

!

vlan 20

name Servers

Host Configuration

Host A (VLAN 10)

IP: 192.168.10.10

GW: 192.168.10.1

Host B (VLAN 20)

IP: 192.168.20.20

GW: 192.168.20.1

Validation

From Host A:

ping 192.168.20.20

From CORE1:

show ip route

show vlan

show interfaces vlan 10

ping 192.168.10.10

ping 192.168.20.20

\- Why Static Routing Here?

Because all routing is done locally on the CORE switch via SVIs.

There's no need for OSPF, BGP, or other protocols — ideal for small environments.
