# Advanced - Lvl.3

### Install Algorand node

* Install any type of official binaries for Algorand node (main/test net)\
  _(this is advanced level so go figure this stuff yourself)_
* Stop the node
* Add Voi testnet relays do node's config.json
* Overwrite genesis.json file with the one attached below
* Start your node

### Fast catch-up&#x20;

{% hint style="info" %}
Sync node in minutes - for non-archival nodes only
{% endhint %}

<pre class="language-bash"><code class="lang-bash"><strong>sudo apt install -y jq 
</strong>goal node catchup $(curl -s https://voitest-api.algorpc.pro/v2/status|jq -r '.["last-catchp
oint"]')
</code></pre>

### Voi testnet relays

Add/replace DNSBootstrapID to your node's `config.json`

`"DNSBootstrapID": "<network>.voi.network"`

Your `config.json` might now look like :

```json
{
        "Archival": false,
        "EndpointAddress": ":8181",
        "CatchpointInterval": 0,
        "AccountsRebuildSynchronousMode": 0,
        "LedgerSynchronousMode": 0,
        "CadaverSizeTarget": 0,
        "GossipFanout": 5,
        "DNSBootstrapID": "<network>.voi.network"
}
```

### Voi testnet Genesis file

Replace genesis.json with the file attached below

{% file src="../../.gitbook/assets/genesis (1).json" %}
genesis.json
{% endfile %}

```json
{
  "alloc": [
    {
      "addr": "7777777777777777777777777777777777777777777777777774MSJUVU",
      "comment": "RewardsPool",
      "state": {
        "algo": 100000,
        "onl": 2
      }
    },
    {
      "addr": "FEESNKYO7TE5LC6SSIQJQ4ZDGYIFGQ26MP3BNEW5TIM54BWGR3PFIFJ2AA",
      "comment": "FeeSink",
      "state": {
        "algo": 100000,
        "onl": 2
      }
    },
    {
      "addr": "DSKWPVJ2MDJIURKS5J7XZC76G3FUFB7PF5VLS6KLAUCFNOQ6HWYZMZNB2Y",
      "comment": "Wallet1",
      "state": {
        "algo": 100000000,
        "onl": 1,
        "sel": "iAwog0Lritehn/CufqnQAJSqkBbtaC9mNUHS2WlbM3w=",
        "stprf": "q2lWVvlCnvdNlKB3iYRfvcLHKLNu0T+KW74sOZXjYsmnFwt/IoAVQliBai96P06BHWhV/o4sT5QcTeDcmwxizw==",
        "vote": "O2lA3hI5Mn4I6d+BnZPunoyv/RuJ3WMNN0fGk284YJI=",
        "voteKD": 10000,
        "voteLst": 3000000
      }
    },
    {
      "addr": "I4SUO77NG5FPUFCJW5YQVLQ5EGD3LZ3I3UG7WRAPGAESQEUQST4GBREBAA",
      "comment": "WalletF",
      "state": {
        "algo": 9999999899800000
      }
    }
  ],
  "fees": "FEESNKYO7TE5LC6SSIQJQ4ZDGYIFGQ26MP3BNEW5TIM54BWGR3PFIFJ2AA",
  "id": "v1",
  "network": "voi-test",
  "proto": "https://github.com/algorandfoundation/specs/tree/44fa607d6051730f5264526bf3c108d51f0eadb6",
  "rwd": "7777777777777777777777777777777777777777777777777774MSJUVU"
}
```
