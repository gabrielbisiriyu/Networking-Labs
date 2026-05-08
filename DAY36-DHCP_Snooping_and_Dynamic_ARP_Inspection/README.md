# DHCP Snooping and Dynamic ARP Inspection (DAI) Lab

## Objective
To configure DHCP Snooping and Dynamic ARP Inspection (DAI), simulate ARP spoofing behavior, and observe how DAI protects the network against invalid ARP messages.

## Topology
- R1 configured as DHCP server
- SW1 and SW2 configured with DHCP Snooping and DAI
- PC1, PC2, and PC3 received IP addresses dynamically
- A "Hacker" PC was introduced to simulate ARP spoofing behavior

## Configurations Performed
- Configured R1 as DHCP server
- Excluded 192.168.1.1 - 192.168.1.9 from DHCP pool
- Configured DHCP Snooping on SW1 and SW2
- Configured uplink interfaces as DHCP Snooping trusted ports
- Enabled Dynamic ARP Inspection on the switches
- Configured sw1 g0/1-2 as DAI trusted ports & sw2 g0/1 as DAI trusted ports

## Initial Testing
PC1, PC2, and PC3 successfully received:
- IP addresses
- Default gateway
- DHCP bindings

Connectivity tests were performed to populate:
- ARP tables
- DHCP Snooping binding tables

## Simulated Attack
The Hacker PC spoofed PC1's IP address (192.168.1.10).

After the spoofing attempt:
- PC3 updated its ARP table with the Hacker PC's MAC address after the Hacker oinged it.
- Traffic intended for PC1 was redirected toward the attacker
- In Simulation Mode, ICMP replies from PC3 were sent to the Hacker PC instead of PC1

This demonstrated ARP spoofing/poisoning behavior that could potentially enable a man-in-the-middle attack.

## DAI Observation
Initially, the attacker could still communicate with devices even after DAI was enabled.

After further testing, I realized this happened because devices already had valid ARP entries cached in their ARP tables. Since no new ARP requests were being generated, DAI had nothing to inspect.

Once I cleared the ARP tables on PC1 and Hacker's PC:
- The spoofed ARP behavior was blocked
- The Hacker PC's ping attempts failed
- PC1 could coommunicate normally because its ARP sender IP and MAC addresses matched an entry in the DHCP Snooping binding table

## Important Takeaways
- DAI only validates ARP messages
- Existing ARP cache entries can allow spoofed communication to temporarily continue
- DHCP Snooping and DAI work together to validate legitimate IP-to-MAC bindings
- MAC addresses themselves can also be spoofed, so DAI is not a complete security solution by itself

## Screenshots
1. DHCP Snooping Binding Table
2. PC3 ARP Table Before Attack
3. PC3 ARP Table After Spoofing
4. PC3 ARP Table After DAI
5. Failed Ping Attempt from Hacker PC
6. Network Topology
