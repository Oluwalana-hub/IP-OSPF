# IP-OSPF

Multi-Area OSPF and DR/BDR Election
In this lab, I configured multi-area OSPF, using Area 0 as the backbone and an Area Border Router (ABR) to connect it to another area.
I also tuned the DR/BDR election on an Ethernet segment using interface priority:
interface GigabitEthernet0/0
 ip ospf priority 255

OSPF elects the eligible router with the highest interface priority as DR. If priorities tie, the highest router ID wins.
- Priority 0: The router cannot become DR or BDR, but still participates in OSPF routing.
- Priority 1: The default priority.
- Priority 255: The highest priority, giving the router preference in a new election. It does not guarantee a win if another router also has priority 255.
OSPF elections are non-preemptive: changing priority does not replace an existing DR or BDR immediately.
I verified the results using:
show ip ospf interface GigabitEthernet0/0
show ip ospf neighbor
show ip route ospf

DR/BDR elections occur per eligible network segment, not once per OSPF area.
