

To copy from switch to your pc (or Linux VM):

scp adm_demunt@10.1.0.1:et4_capture.pcap /Users/dietrichd


*** Lab Objective: Start and export a pcap session on a switch in De Munt network ***


Arista switches support running tcpdump from Bash.

Capture on Interface (e.g., Ethernet1)

sudo tcpdump -i et1 -w /mnt/flash/eth1_capture.pcap


Or capture all VLAN 10 traffic:

sudo tcpdump -i et1 -w /mnt/flash/vlan10_traffic.pcap

4. Run a Test (from a host or another switch) e.g.

ping 192.168.10.2


You should see ICMP traffic flowing through the switch and being captured.

5. Stop the Capture

Inside the Bash shell:

Press Ctrl+C to stop

6. Export the PCAP File

To move the .pcap off the switch for Wireshark analysis:

copy flash:eth1_capture.pcap scp://user@host/path/


Or use TFTP, USB, or curl if appropriate.




Notes:

tcpdump is not EOS CLI — you must enter Bash shell (bash) first

You can capture on physical, VLAN, or even management interfaces


Use tcpdump -nn -vvv to see live verbose output (omit -w)


You can filter by protocol: icmp, tcp, port 80, etc.

PCAP files saved to /mnt/flash/ persist across reloads



- One-liner to Check Captures Without Exporting 

bash # sudo tcpdump -nn -r /mnt/flash/eth1_capture.pcap


Why It's Useful ?

Arista switches make in-band traffic inspection easy without SPAN

Excellent for security troubleshooting, latency analysis, or protocol debugging

Especially powerful when paired with event-handlers or LANZ triggers


