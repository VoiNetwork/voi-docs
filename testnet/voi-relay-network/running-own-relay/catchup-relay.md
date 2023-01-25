# Catchup Relay

A catchup relay is a new (Q1 2023) type of node that has very low resource usage and can be run on the same hardware as catchup nodes.

{% hint style="info" %}
Official source code and binaries for this type of node will be available in Q1'23
{% endhint %}

### Requirements

[Hardware requirement ](./)are the same as a normal catchup node. As the network grows, in terms of number of normal nodes and traffic,  the requirement for network egress (monthly traffic quota) will be increasing.

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

* Install and sync a normal Voi [catchup node](../../node-running/advanced-lvl.2.md)&#x20;
* Add these config changes and restart your node

```bash
# disable archival behaviour
algocfg set -p Archival -v false
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

