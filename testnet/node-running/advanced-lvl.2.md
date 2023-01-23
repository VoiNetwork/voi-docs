# ⚡ Advanced - Lvl.2

## Installing Voi testnet node

{% hint style="info" %}
This guide will help you install non-archival, catch-up node that you can use for development, account management or participation&#x20;
{% endhint %}

### <mark style="color:orange;">Overview</mark>

* Install Algorand node binaries
* Switch network to testnet Voi
* Enable anonymous telemetry
* Do a fast catch-up

### <mark style="color:orange;">Step 1 : Install any type of official binaries for Algorand node</mark>&#x20;

This this is advanced level guide and it assumes you already have an Algorand mainnet/testnet node installed on Linux/Ubuntu. You can try some of the guides here:

{% embed url="https://d13.co/set-up-algorand-participation-node-on-oracle-cloud-free/" %}

{% embed url="https://developer.algorand.org/docs/run-a-node/setup/install/" %}

### <mark style="color:orange;">Step 2 : Switch network to Voi</mark>

#### Stop your node either with&#x20;

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
algocfg set -p GossipFanout -v 9
```

_Note: You can use these commands as provided, no need to replace `<network>`._

Your `/var/lib/algorand/config.json` should look like :

```json
{
        "GossipFanout": 9,
        "DNSBootstrapID": "<network>.voi.network"
}
```

#### Overwrite /var/lib/algorand/genesis.json file with the one attached below

{% file src="../../.gitbook/assets/genesis.json" %}
genesis.json
{% endfile %}

You can also do it with this command:

```bash
sudo curl -s -o /var/lib/algorand/genesis.json https://voitest-api.algorpc.pro/genesis
```

### <mark style="color:orange;">Step 3 : Enable anonymous telemetry</mark>

{% hint style="info" %}
This step is optional but will help us monitor the network and will give you access to your node voting stats on Voi's monitoring portal.
{% endhint %}

#### :point\_right: Enable telemetry :point\_left:

```bash
diagcfg telemetry enable
```

### <mark style="color:orange;">Step 4 : Fast catch-up</mark>

{% hint style="info" %}
This will sync you non-archival node in minutes&#x20;
{% endhint %}

#### Start your node either with&#x20;

```
goal node start
```

or

```bash
systemctl start algorand
```

#### Do the fast catch-up

<pre class="language-bash"><code class="lang-bash"><strong>sudo apt install -y jq 
</strong>goal node catchup $(curl -s https://voitest-api.algorpc.pro/v2/status|jq -r '.["last-catchp
oint"]')
</code></pre>

### <mark style="color:orange;">Step 5 : Watch your node syncing</mark>

You can now watch how you node syncs with this comman (ctrl-c to stop):

```bash
watch goal node status
```

You node is synced once `Sync Time:` reads `0.0s`
