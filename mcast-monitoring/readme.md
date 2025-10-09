Multicast Monitoring & Troubleshooting Lab

Objective

This lab will guide you through **verification-only** tasks to determine whether multicast is functioning correctly in a live environment using IGMP Snooping (v2/v3) and PIM multicast routing.

You will:

- Inspect IGMP snooping tables
- Check multicast group memberships
- Validate PIM neighbor relationships
- Analyze multicast forwarding paths
- Identify potential issues in multicast traffic delivery

---

You will need SSH access to the switches in order to do this.

There is an admin "De Munt" access that has been provided by Dietrich.

Your virtual machine in the Lab has access to our jump-server. You are able to ssh using this host to any of the OOB-IP addresses of the switches.
---

Lab Tasks with Commands

1. Check IGMP Snooping on L2 Switches

show ip igmp snooping

Confirms IGMP snooping is enabled globally.

show ip igmp snooping vlan <VLAN-ID>

Checks snooping status per VLAN and displays router ports and querier.

show ip igmp snooping groups vlan <VLAN-ID>

Lists multicast group memberships and the interested interfaces.

---

2. Verify IGMP Group Memberships

On the L3 switch or router:

show ip igmp groups

Displays hosts joined to multicast groups, interface, version (v2/v3), and timer.

---

3. Check PIM Neighbor Relationships

show ip pim neighbor

Validates that PIM adjacency is established and stable.

---

4. Inspect Multicast Routing Table

show ip mroute

Shows (*,G) and (S,G) entries, incoming and outgoing interfaces, and timers.

Look for:
- Correct RPF (Reverse Path Forwarding) interface
- Non-empty OIL (Outgoing Interface List)

---

️ 5. Trace the Multicast Tree

show ip mroute | include <group-address>

Or:

show ip mroute <group> <source>

Verifies correct RPF and multicast tree construction.

---

6. Monitor Active Traffic

show interfaces counters rates

Look for traffic on interfaces involved in multicast forwarding.

Optional:

monitor capture <name> interface <intf> match ip multicast any any

---

7. Validate PIM RP Mapping (for PIM-SM)

show ip pim rp mapping

Ensures RP is known and reachable.


8. Check Logs and Events

show logging | include IGMP|PIM

Look for joins/leaves, neighbor timeouts, or RPF failures.

---

Show All Groups and Interfaces (Summary)

show ip igmp snooping summary

show ip pim interface

---

Reflection Questions

1. Are IGMP joins visible and mapped to the correct ports?
2. Are PIM neighbors stable on all interfaces?
3. Is the multicast routing table showing expected (S,G) entries?
4. Are outgoing interfaces populated for multicast routes?
5. Is the RP reachable and correctly mapped (for PIM-SM)?
6. Is traffic observed on interfaces as expected?

---

Success Criteria

- IGMP snooping shows receivers on correct ports.
- PIM adjacencies are UP and stable.
- Multicast routing entries exist with correct IIF and OIL.
- Traffic is visible in interface counters or capture.
- RP and PIM behavior match expected configuration.

