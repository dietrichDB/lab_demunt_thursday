A. Wireshark Arista Profile

OBJECTIVES OF THE PROFILE

Highlight VLAN, ARP, ICMP, MLAG, and VARP-related traffic

Color-code key packet types for quick scanning

Pre-define filters and column layouts that help with:

Troubleshooting connectivity

Analyzing MAC/IP flows

Debugging MLAG peer-link behavior

Watching routing via SVIs (VARP)


️ PROFILE CONTENTS (You Will Get)

1. Custom Columns

To improve visibility of L2/L3 data paths:

Column Name	Field
VLAN	vlan.id
Src MAC	eth.src
Dst MAC	eth.dst
Src IP	ip.src
Dst IP	ip.dst
Protocol	frame.protocols
TTL	ip.ttl
TCP Flags	tcp.flags

2. Coloring Rules


Color	Filter	Use Case
🔵 Blue	vlan	VLAN-tagged traffic
🟢 Green	icmp	ICMP traffic (ping, traceroute)
🟡 Yellow	arp	ARP requests/replies
🔴 Red	tcp.analysis.retransmission	TCP retransmissions (drops)
🟣 Purple	ether dst == 01:00:0c:cc:cc:cc	MLAG/VARP multicast
⚫ Gray	`stp	


3. Display Filters (Quick-Access Bookmarks)

Pre-configured filter buttons:

icmp

arp

vlan

tcp.port == 22 || 443 (mgmt plane)

eth.dst == 01:00:0c:cc:cc:cc (MLAG/VARP)

ip.addr == 192.168.10.1 (editable)


INSTALL INSTRUCTIONS

Profile Path:

On Linux/Mac:

~/.config/wireshark/profiles/Arista/


On Windows:

%APPDATA%\Wireshark\profiles\Arista\

Contents of the .zip:


Arista/
├── colorfilters
├── dfilters
├── recent
├── preferences
├── columns


You just need to unzip it to the Wireshark profiles folder and select the profile via:

Wireshark → Edit → Configuration Profiles → Arista



2. Wireshark multicast profile

What's Inside


Color Filters:

 Multicast IP (224.0.0.0/4) – Green

IGMP (Group Join/Leave) – Cyan

PIM (Protocol Independent Multicast) – Magenta

MLAG/VARP Multicast (01:00:0c:cc:cc:cc) – Purple

General Broadcast (ff:ff:ff:ff:ff:ff) – Yellow



Display Filters (quick search):

Multicast IP

IGMP

PIM

Broadcast

MLAG-related multicast

Columns:

VLAN ID

Src/Dst MAC & IP

TTL

Protocols
