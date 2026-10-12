

\# LAB 1 - Basic LAN Network Infrastructure



\*\*Course:\*\* Enterprise Networks 1  

\*\*Table:\*\* 07  

\*\*Date:\*\* 12 October 2026  

\*\*Repository:\*\* Network-Expert  

\*\*Branch:\*\* LAB-1



\## 1. Objective



Configure and verify a basic LAN infrastructure using a Cisco ISR4221 router and a Cisco Catalyst C9200L switch.



The lab covers:

\- VLAN configuration

\- 802.1Q trunking

\- Router-on-a-stick

\- Switch management

\- OSPFv2 routing

\- DHCP relay

\- Connectivity and DNS verification



\## 2. Network Topology



```text

&#x20;            Central Lab Network

&#x20;              10.199.66.192/27

&#x20;                     |

&#x20;              10.199.66.200

&#x20;                     |

&#x20;               Gi0/0/1

&#x20;            +----------------+

&#x20;            | Cisco ISR4221  |

&#x20;            | Router R01     |

&#x20;            | 10.199.66.207  |

&#x20;            +----------------+

&#x20;               Gi0/0/0

&#x20;                     |

&#x20;                802.1Q Trunk

&#x20;                     |

&#x20;               Gi1/0/24

&#x20;            +----------------+

&#x20;            | Cisco C9200L   |

&#x20;            | Switch SW01    |

&#x20;            | 172.16.7.4     |

&#x20;            +----------------+

&#x20;               Gi1/0/11

&#x20;                     |

&#x20;                 VLAN 47

&#x20;                     |

&#x20;              Windows Laptop

&#x20;               172.16.7.213

```



\## 3. VLAN Addressing



| VLAN | Name | Network | Router IP |

|---|---|---|---|

| 17 | Management | 172.16.7.0/26 | 172.16.7.2 |

| 27 | VM-Hosts | 172.16.7.64/26 | 172.16.7.66 |

| 37 | Appliance-Servers | 172.16.7.128/26 | 172.16.7.130 |

| 47 | Data-Users | 172.16.7.192/26 | 172.16.7.194 |

| 99 | Native-Vlan | N/A | N/A |



\## 4. Router Configuration



Four subinterfaces were configured on Gi0/0/0 using IEEE 802.1Q encapsulation.



The external interface Gi0/0/1 was configured with 10.199.66.207/27.



OSPFv2 settings:

\- Process ID: 7

\- Router ID: 7.7.7.7

\- Area: 0

\- Reference bandwidth: 10000 Mbps

\- Passive LAN interfaces

\- Active OSPF on Gi0/0/1



A DHCP relay was configured on VLAN 47 to forward requests to 10.199.64.66.



Configuration: \[R1.cfg](configs/R1.cfg)



\## 5. Switch Configuration



Configured VLANs: 17, 27, 37, 47 and 99.



\- Gi1/0/24: 802.1Q trunk to router

\- Native VLAN: 99

\- Gi1/0/11: access VLAN 47

\- Management SVI: VLAN 17

\- Switch IP: 172.16.7.4/26

\- Default gateway: 172.16.7.2



Configuration: \[SW1.cfg](configs/SW1.cfg)



\## 6. Verification



Successful tests:

\- Router-to-switch management ping

\- Two FULL OSPF neighbors

\- OSPF routes and default route received

\- DHCP address assignment on VLAN 47

\- Laptop-to-gateway ping

\- Laptop-to-internet ping

\- DNS resolution



See \[test-results.md](verification/test-results.md).



\## 7. Important Cisco Commands



```text

show ip interface brief

show vlan brief

show interfaces trunk

show cdp neighbors

show ip ospf neighbor

show ip ospf interface brief

show ip route ospf

show ip protocols

show running-config

```



\## 8. Notes



The lab equipment has an automated classroom reset mechanism. The configuration files in this repository document the relevant lab settings, not the complete device configuration.



Only VLAN 47 was verified with a physical client. Other VLANs were configured but not individually tested with clients.



\## 9. Conclusion



The tested basic LAN infrastructure is operational.



VLAN trunking, router-on-a-stick, OSPF routing, DHCP relay, gateway connectivity, internet access and DNS resolution were successfully demonstrated.



