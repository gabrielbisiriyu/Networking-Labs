# Extended ACL Lab

## Objective
To configure extended ACLs to control traffic between hosts and servers according to network policies.

## Network Policies
- Hosts in 172.16.2.0/24 cannot communicate with PC1.
- Hosts in 172.16.1.0/24 cannot access the DNS service on SRV1.
- Hosts in 172.16.2.0/24 cannot access HTTP/HTTPS services on SRV2.

## Configurations Performed
- Created extended ACLs to filter traffic based on source, destination, and service (TCP/UDP).
- Applied ACLs to the correct router interfaces in the inbound/outbound direction.
- Verified access control by testing pings and service availability from PCs.


## Observations
- `show access-lists` confirmed ACLs were active and matched traffic.
- PC1 was able/unable to ping as expected before and after ACLs.
- DNS and HTTP/HTTPS access was properly restricted for the specified networks.

## Screenshots
1. ACL entries: `show access-lists`  
2. Ping/DNS test before & after  
3. HTTP test before & after  

## Lessons Learned
- Extended ACLs allow precise control of network traffic by source, destination,protocol,port numbers.  
- Placement of ACLs on the correct interface and direction is crucial.  
- Testing before and after ACL implementation ensures rules work as intended.
