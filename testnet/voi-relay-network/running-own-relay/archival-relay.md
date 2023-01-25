# Archival Relay

An archival relay is type of node that stores the whole blockchain history. The I/O requirements are proportional to the amount of history and current transaction traffic and require datacenter type NVMe drives.&#x20;

### Requirements

[Hardware requirement ](../running-own-relay.md)are at least 4 times as a normal catchup node. As the network grows, in terms of number of normal nodes and traffic,  the requirement for network egress (monthly traffic quota) will be increasing.&#x20;

Your relay will be calculating catchups every 10k rounds - this proces is very CPU and I/O intensive

{% hint style="warning" %}
Your node and internet connection need to be up 99.5% of the time.\
That is up to 3h downtime a month!

Running obsolete node version counts as downtime.
{% endhint %}

### Setup

#### Prerequisites

* You need a public name (PublicAddress) for your node. \
  This name is going to be visible in the public SRV relay set.
* Your firewall needs to allow incoming TCP connections to port 4161 (testnet)

#### Node configuration

* Install a normal Voi [catchup node](../../node-running/advanced-lvl.2.md) but **do not sync it yet**
* Add these config changes and restart your node

```bash
# enable archival behaviour
algocfg set -p Archival -v true
# enable relay mode
algocfg set -p NetAddress "0.0.0.0:4161"
# make it hyperconnected
algocfg set -p GossipFanout 10
# enable metrics
algocfg set -p EnableMetricReporting true
# name the relay to prevent self peering
algocfg set -p PublicAddress "r-co01.test.voi.network:4161"
# make sure we are on voi network
algocfg set -p DNSBootstrapID -v "<network>.voi.network"
# enable serving blocks
algocfg set -p EnableBlockService true
# enable ledger service
algocfg set -p EnableLedgerService true
# Tune for top#200 stake survival during a storm
algocfg set -p BroadcastConnectionsLimit 200
algocfg set -p ConnectionsRateLimitingCount 30
algocfg set -p ConnectionsRateLimitingWindowSeconds 1
# enable telemetry
diagcfg telemetry enable
```

### Joining the network

Once your relays is up and running the core team is going to add your PublicAddress to the list of relays in the Voi network bootstrap SRV record.&#x20;

You can check if your relay is added to the set with this command:

```bash
dig +short @1.1.1.1 SRV _algobootstrap._tcp.voi-test.voi.network.
```

```bash
1 1 4161 r-co00.test.voi.network.
1 1 4161 r-co01.test.voi.network.
1 1 4161 r-co02.test.voi.network.
1 1 4161 r-co03.test.voi.network.
1 1 4161 r-co04.test.voi.network.
1 1 8080 r-co05.test.voi.network.
1 1 8080 r-co06.test.voi.network.
1 1 8080 r-co07.test.voi.network.
1 1 8080 r-co08.test.voi.network.
```

