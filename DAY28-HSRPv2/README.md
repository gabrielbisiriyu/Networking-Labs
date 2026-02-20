# HSRPv2 Gateway Redundancy Lab
## Objective
To configure HSRPv2 for first-hop redundancy, implement priority tuning with preemption, and verify failover behavior.

## Initial Test
Default gateway on PCs was configured as the physical router R1's IP address.
Ping to 8.8.8.8 was successful.

## Configuration Performed

Configured HSRPv2 on R1 and R2

Raised R1 priority above default (100)

Lowered R2 priority below default

Enabled preemption

Configured Virtual IP as default gateway on PCs

## Verification
### Active/Standby Status

`show standby brief`

## Failover Test

After shutting down R1:

R2 became Active

Ping to 8.8.8.8 remained successful

After turning R1 back on:

R1 resumed Active role due to preemption

## Lessons Learned

HSRP provides gateway redundancy without changing host configuration

Preemption allows higher priority router to reclaim Active status
