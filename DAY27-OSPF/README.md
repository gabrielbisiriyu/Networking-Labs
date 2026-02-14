# Lab Title: Basic OSPF Configuration with Default Route Injection
## Objective

To configure OSPF , set passive interfaces, adjust reference bandwidth, configure an ASBR, and observe OSPF Hello packets.

## Key Configurations Performed

-- Enabled OSPF 

-- Configured loopback interfaces on each router

-- Set reference bandwidth so FastEthernet cost = 100 while GigabitEthernet = 10

-- Configured R1 as ASBR

-- Advertised default route into OSPF domain

-- Verification Commands

-- show ip ospf neighbor

-- show ip route

-- show ip ospf interface

## Important Observations

-- R4 received a default route marked as O*E2

-- Hello packets included Router ID, Area ID, Hello interval, Dead interval, Neighbor list



