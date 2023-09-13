# ⚡ ADV: Linux terminal install

## Installing Voi testnet node

{% hint style="info" %}
This guide will help you install non-archival, catch-up node that you can use for development, account management or participation
{% endhint %}

### <mark style="color:orange;">Overview</mark>

* Install Algorand node binaries
* Switch network to testnet Voi
* Enable anonymous telemetry
* Do a fast catch-up

### <mark style="color:orange;">Step 1 : Install any type of official binaries for Algorand node</mark>

This this is advanced level guide and it assumes you already have an Algorand mainnet/testnet node installed on Linux/Ubuntu. You can try some of the guides here:

{% embed url="https://d13.co/set-up-algorand-participation-node-on-oracle-cloud-free/" %}

{% embed url="https://developer.algorand.org/docs/run-a-node/setup/install/" %}

### <mark style="color:orange;">Step 2 : Switch network to Voi</mark>

#### Stop your node either with

```
goal node stop
```

or

```bash
systemctl stop algorand
```

#### Add Voi relays to node's config.json

```bash
algocfg set -p DNSBootstrapID -v "<network>.voi.network"
algocfg set -p GossipFanout -v 8
algocfg set -p EnableCatchupFromArchiveServers -v true
```

_Note: You can use these commands as provided, no need to replace `<network>`._

Your `/var/lib/algorand/config.json` should look like :

```json
{
        "GossipFanout": 8,
        "DNSBootstrapID": "<network>.voi.network",
        "EnableCatchupFromArchiveServers": true
}
```

#### Overwrite /var/lib/algorand/genesis.json file with Voi genesis

You can also do it with this command:

```bash
sudo curl -s -o /var/lib/algorand/genesis.json https://testnet-api.voi.nodly.io/genesis
```

Or you can download the genesis.json [here](https://testnet-api.voi.nodly.io/genesis) as well.&#x20;

### <mark style="color:orange;">Step 3 : Enable telemetry</mark>

Enabling telemetry is optional for normal participation but required if you want to prove your node's performance. You can name your node but it is not required.&#x20;

```
# name you node
diagcfg telemetry name -n "Lab.voi"
```

```
# enable telemetry
diagcfg telemetry enable
```

Confirm telemetry is configured:

```
root@alab:~# diagcfg telemetry status 

Remote logging is enabled. 
Node = Lab, Guid = 12455678-7434-4423-91ee-0a3500ec5680
```

### <mark style="color:orange;">Step 4 : Fast catch-up</mark>

{% hint style="info" %}
This will sync you non-archival node in minutes
{% endhint %}

#### Start your node either with

```
goal node start
```

or

```bash
systemctl start algorand
```

#### Do the fast catch-up

<pre class="language-bash"><code class="lang-bash"><strong>sudo apt install -y jq 
</strong>goal node catchup $(curl -s https://testnet-api.voi.nodly.io/v2/status|jq -r '.["last-catchpoint"]')
</code></pre>

### <mark style="color:orange;">Step 5 : Watch your node syncing</mark>

You can now watch how you node syncs with this comman (ctrl-c to stop):

```bash
watch goal node status
```

You node is synced once `Sync Time:` reads `0.0s`



### <mark style="color:orange;">Peer2Peer relay discovery (TBA)</mark>

{% hint style="info" %}
P2P relay discovery allows connection to fully permissionless network without centrally managed relays. Watch this place for P2P setup info.
{% endhint %}
