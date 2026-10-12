

\# LAB 1 - Verification Results



\*\*Course:\*\* Enterprise Networks 1  

\*\*Lab:\*\* Basic LAN Network Infrastructure  

\*\*Table:\*\* 07  

\*\*Date:\*\* 12 October 2026



\## 1. Router and Switch Connectivity



| Test | Result | Status |

|---|---|---|

| Router Gi0/0/0 to Switch Gi1/0/24 | Connected | PASS |

| Router Gi0/0/1 to central network | Connected | PASS |

| Switch management IP | 172.16.7.4/26 | PASS |

| Switch to Router ping | 5/5 replies | PASS |



\## 2. VLAN Configuration



| VLAN | Name | Network |

|---|---|---|

| 17 | Management | 172.16.7.0/26 |

| 27 | VM-Hosts | 172.16.7.64/26 |

| 37 | Appliance-Servers | 172.16.7.128/26 |

| 47 | Data-Users | 172.16.7.192/26 |

| 99 | Native-Vlan | No IP network |



Trunk interface: Gi1/0/24  

Native VLAN: 99  

Allowed VLANs: 17,27,37,47,99  

Spanning Tree: Forwarding



\## 3. OSPF Verification



OSPF Process ID: 7  

Router ID: 7.7.7.7  

Area: 0  

Reference Bandwidth: 10000 Mbps



| Neighbor ID | Address | State |

|---|---|---|

| 10.10.10.10 | 10.199.66.210 | FULL/BDR |

| 255.255.255.255 | 10.199.66.200 | FULL/DR |



OSPF routes learned:

\- 172.16.10.0/26

\- 172.16.10.64/26

\- 172.16.10.128/26

\- 172.16.10.192/26

\- 0.0.0.0/0 via 10.199.66.200



Result: PASS



\## 4. DHCP Verification



Client: Windows laptop  

Switch port: Gi1/0/11  

VLAN: 47



IPv4 address: 172.16.7.213  

Default gateway: 172.16.7.194  

DNS server: 10.199.64.66  

DHCP relay: 10.199.64.66



Result: PASS



\## 5. Connectivity Tests



| Test | Result | Status |

|---|---|---|

| Laptop to 172.16.7.194 | 4/4 replies | PASS |

| Laptop to 8.8.8.8 | 4/4 replies | PASS |

| Router to 8.8.8.8 | 5/5 replies | PASS |

| Router to 10.199.64.66 | 5/5 replies | PASS |

| DNS lookup google.com | Resolved | PASS |



\## 6. Conclusion



The tested LAB 1 network infrastructure is operational.



\- VLANs and 802.1Q trunking configured.

\- Inter-VLAN routing interfaces configured.

\- OSPF neighbors established and routes learned.

\- DHCP relay functioning for VLAN 47.

\- Gateway, internet connectivity and DNS verified.



Other access ports and VLANs have not been individually tested.



