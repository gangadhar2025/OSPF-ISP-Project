ISP Real-Time Network Project

This repository showcases an ISP network topology implemented using GNS3, featuring:

    OSPF Routing with multiple areas.
    DHCP server configuration with relay agents.
    Integration of DNS and HTTP servers for complete functionality.

    Below is a practical README.md file for your GitHub repository. It is designed to guide users step-by-step through your ISP OSPF network project.
ISP Real-Time Network Project

This repository showcases an ISP network topology implemented using GNS3, featuring:

    OSPF Routing with multiple areas.
    DHCP server configuration with relay agents.
    Integration of DNS and HTTP servers for complete functionality.

Topology Overview
Network Components:

    Routers:
        R1 (Area 1 router)
        R2 (ABR between Areas 0 and 1)
        R3 (ABR between Areas 0 and 2)
        R4 (Area 2 router, connected to servers)

    Switches:
        Switch1 (Colony Customers Phase 1)
        Switch2 (Colony Customers Phase 2)
        Switch3 (Office Server Network)

    Servers:
        DHCP Server: 10.100.11.11
        DNS Server: 10.100.11.111
        HTTP Server: 10.100.11.211

    Customer Devices:
        Phase 1: Customer1 and Customer2
        Phase 2: Customer3A and Customer3B

Key Configurations
1. OSPF Routing
Router R1 (Area 1):

router ospf 1
network 10.100.12.0 0.0.0.255 area 0
network 192.168.14.0 0.0.0.255 area 1

Router R2 (Area 0 and 1):

router ospf 1
network 10.100.12.0 0.0.0.255 area 0
network 192.168.15.0 0.0.0.255 area 1

Router R3 (Area 0 and 2):

router ospf 1
network 10.100.34.0 0.0.0.255 area 0
network 10.100.11.0 0.0.0.255 area 2

2. DHCP Server Configuration
DHCP Pools:

# Pool for Phase 1 (Colony Customers)
subnet 192.168.14.0 netmask 255.255.255.0
range 192.168.14.2 192.168.14.254
option routers 192.168.14.1

# Pool for Phase 2 (Colony Customers)
subnet 192.168.15.0 netmask 255.255.255.0
range 192.168.15.2 192.168.15.254
option routers 192.168.15.1

3. DHCP Relay Agent
Switch3 Configuration:

interface e0
ip helper-address 10.100.11.11

4. Verification Commands
On Router R1 (OSPF Neighbor Verification):

show ip ospf neighbor

Ping Test for Connectivity:

ping 10.100.11.111   # DNS Server
ping 10.100.11.211   # HTTP Server

Check IP Address Assignment (Customer PC):

ip dhcp  # For dynamically assigned IP

Learnings and Insights

    Designed and tested OSPF multi-area architecture for ISP scalability.
    Successfully implemented DHCP relay for multi-subnet dynamic IP allocation.
    Gained practical knowledge of real-world ISP network challenges and solutions.

