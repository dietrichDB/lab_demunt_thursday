Configure the following Parameters for your lab:

1. Add a user adm_youruser with a complex password, disable the admin user for each switch.
2. Configure one VLAN 1000 on all switches with all used interfaces in it (except from your mgmnt interface).
3. Configure mstp as a spanning-tree topology, spine should be the root bridge, leafs should not become root-bridge.
4. Give each switch a unique IP-address in VLAN 1000, document the chosen IP addresses and -range.
5. Check if the switches can ping eachother.
6. Check which ports have been shut in the spanning-tree topology.
7. Save your lab;-) and graph your set-up to draw.io using containerlab graph.
8. Document your setup in git on your own account.
9. Bonus for those who are easily bored:

You can connect to the local linux machines using docker exec -it <container-name/id> bash (for example docker exec -it clab-3clos-client1 bash)
Can you:
  - ping to your switches and the other VM using this bash?
  - Configure ssh so you can directly ssh into that vm? (you will need ssh installed and an user added... and maybe more;-))


This is BONUS so don't go too far;-)
