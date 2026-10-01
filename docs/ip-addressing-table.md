\# IP Addressing Table



\## VLAN Networks



| VLAN | Department | Network | Subnet Mask | Default Gateway |

|------|------------|---------|-------------|-----------------|

| 10 | HR | 192.168.10.0/24 | 255.255.255.0 | 192.168.10.1 |

| 20 | IT | 192.168.20.0/24 | 255.255.255.0 | 192.168.20.1 |

| 30 | Finance | 192.168.30.0/24 | 255.255.255.0 | 192.168.30.1 |



\---



\## Router Interfaces



\### R1



| Device | Interface | IP Address | Subnet Mask | Purpose |

|--------|-----------|------------|-------------|---------|

| R1 | GigabitEthernet0/0.10 | 192.168.10.1 | 255.255.255.0 | HR Gateway |

| R1 | GigabitEthernet0/0.20 | 192.168.20.1 | 255.255.255.0 | IT Gateway |

| R1 | GigabitEthernet0/0.30 | 192.168.30.1 | 255.255.255.0 | Finance Gateway |

| R1 | GigabitEthernet0/1 | 10.0.12.1 | 255.255.255.252 | R1-R2 OSPF Link |

| R1 | GigabitEthernet0/2 | 10.0.31.2 | 255.255.255.252 | R1-R3 OSPF Link |



\### R2



| Device | Interface | IP Address | Subnet Mask | Purpose |

|--------|-----------|------------|-------------|---------|

| R2 | GigabitEthernet0/1 | 10.0.12.2 | 255.255.255.252 | R2-R1 OSPF Link |

| R2 | GigabitEthernet0/2 | 10.0.23.1 | 255.255.255.252 | R2-R3 OSPF Link |



\### R3



| Device | Interface | IP Address | Subnet Mask | Purpose |

|--------|-----------|------------|-------------|---------|

| R3 | GigabitEthernet0/1 | 10.0.23.2 | 255.255.255.252 | R3-R2 OSPF Link |

| R3 | GigabitEthernet0/2 | 10.0.31.1 | 255.255.255.252 | R3-R1 OSPF Link |



\---



\## End Devices



| Device | Department | VLAN | IPv4 Address | Default Gateway |

|--------|------------|------|--------------|-----------------|

| PC-HR1 | HR | 10 | 192.168.10.10 | 192.168.10.1 |

| PC-HR2 | HR | 10 | 192.168.10.11 | 192.168.10.1 |

| PC-IT1 | IT | 20 | 192.168.20.10 | 192.168.20.1 |

| PC-IT2 | IT | 20 | 192.168.20.11 | 192.168.20.1 |

| PC-FIN1 | Finance | 30 | 192.168.30.10 | 192.168.30.1 |

| PC-FIN2 | Finance | 30 | 192.168.30.11 | 192.168.30.1 |



\---



\## OSPF Point-to-Point Networks



| Link | Network | Subnet Mask | Device A | IP Address | Device B | IP Address |

|------|---------|-------------|----------|------------|----------|------------|

| R1-R2 | 10.0.12.0/30 | 255.255.255.252 | R1 G0/1 | 10.0.12.1 | R2 G0/1 | 10.0.12.2 |

| R2-R3 | 10.0.23.0/30 | 255.255.255.252 | R2 G0/2 | 10.0.23.1 | R3 G0/1 | 10.0.23.2 |

| R1-R3 | 10.0.31.0/30 | 255.255.255.252 | R1 G0/2 | 10.0.31.2 | R3 G0/2 | 10.0.31.1 |



\---



\## DHCP Addressing



DHCP is provided by R1 for the three departmental VLANs.



| DHCP Pool | Network | Default Gateway | DNS Server |

|-----------|---------|------------------|------------|

| HR | 192.168.10.0/24 | 192.168.10.1 | 8.8.8.8 |

| IT | 192.168.20.0/24 | 192.168.20.1 | 8.8.8.8 |

| FINANCE | 192.168.30.0/24 | 192.168.30.1 | 8.8.8.8 |



\---



\## Addressing Summary



\### Department Networks



\- VLAN 10 → `192.168.10.0/24`

\- VLAN 20 → `192.168.20.0/24`

\- VLAN 30 → `192.168.30.0/24`



\### Router-to-Router Networks



\- R1-R2 → `10.0.12.0/30`

\- R2-R3 → `10.0.23.0/30`

\- R1-R3 → `10.0.31.0/30`



\### Routing Protocol



\- OSPF Area 0



\### DHCP Server



\- R1



\### ACL



\- `IT-SECURITY`

\- IT → Finance traffic is denied

\- IT → HR traffic is permitted

