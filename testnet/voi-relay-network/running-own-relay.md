# Running own relay

### Running relays rulez (WIP)

1. Everyone can apply for running a relay node.&#x20;
2. Candidates must meet the current minimum hardware requirements.&#x20;
3. Candidates are required to fill in a simple form testing their basic consensus knowledge.
4. Relay runners must make their nodes' geo-location public down to the city level.&#x20;
5. New relay nodes are entered into `staging.voi.network` SRV DNS relay set for 3 months.
6. Staging set participates in intra relay traffic exchange but does not handle end-user nodes.
7. Staging set is monitored for TX propagation quality with dedicated transactions. &#x20;
8. On-chain propagation data stats are used to qualify the candidate for listing on the main bootstrap DNS SRV set.
9. Promoted relays are monitored for availability and propagation performance and are subject to automatic delisting.
10. Promoted relays are required to report metrics to Voi.network monitoring solution. (TBA)
