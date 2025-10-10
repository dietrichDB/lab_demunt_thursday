*** Lab Objective ***

- Export pcap you just make
- Open it in WireShark
- Apply Filters & Colors


Usefull Links:

- https://www.wireshark.org/download.html
- https://www.wireshark.org/docs/man-pages/wireshark-filter.html



First Export the Capture

If you captured traffic like so:

sudo tcpdump -i Ethernet1 -w /mnt/flash/eth1_capture.pcap


You'll need to copy it off the switch:

copy flash:eth1_capture.pcap scp://user@your-laptop:/home/user/wireshark_captures/


Then open it in Wireshark:

wireshark eth1_capture.pcap




ANALYSIS POINTERS (Wireshark)




1. Apply Basic Filters

Start with filtering traffic types:

ICMP (pings):

icmp


ARP traffic:

arp


Specific IP:

ip.addr == 192.168.10.1


Show only VLAN-tagged traffic (802.1Q):

vlan





2. Inspect VLAN Tags

When traffic is captured from a trunk port (or access port in a tagged environment), check for 802.1Q headers:

Look for the Protocol: 802.1Q field

It will include:

VLAN ID

Priority Code Point (PCP)

Drop Eligible Indicator (DEI)

This is useful to verify correct tagging of VLAN 10/20/etc.





3. Follow Conversations

Wireshark can group sessions:

TCP streams:
Right Click → Follow → TCP Stream

UDP or ICMP equivalents also have similar options

Helps in debugging application flow between hosts



4. Check Packet Timing / Latency

Use Wireshark I/O Graphs:

Statistics → I/O Graphs

Useful for:

Visualizing packet bursts

Spotting drops or asymmetric flow

Or use:

Statistics → Conversations → Ethernet or IPv4


To find packet/byte count between MAC or IP pairs.




5. Identify Issues

Some typical issues and how to spot them:

Problem	What to Look For in Wireshark
Duplicate frames	Repeated packets with same Seq number or ID
VLAN mis-tagging	Wrong or missing 802.1Q VLAN ID
Unidirectional traffic	Packets only from one side in a conversation
MAC flaps or loops	Repeated source MACs from different ports
Incorrect routing	No ARP replies or wrong gateway MAC responses
Dropped packets	Gaps in TCP Seq, missing replies, TCP Retransmissions
High latency	Look at Time Delta from previous packet in TCP or ICMP streams




6. Colorize Traffic

Set display filters with color rules:

Green for ICMP

Red for TCP retransmissions

Blue for VLAN traffic

Use:

View → Coloring Rules → +Add



Example Use Case: Inter-VLAN Routing Verification

If you ping from 192.168.10.10 to 192.168.20.20:

Check ARP for destination MAC

Look for ICMP Echo → Reply

Confirm SVI MACs from .1 addresses

Validate TTL change (should decrement if routed)
