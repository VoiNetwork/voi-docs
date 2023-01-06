# FAQ

### What is participation ?

👉 Proposing & voting on blocks

* You mark your account(s) holding some Algo as online
* Online accounts participate (via participation keys hosted on nodes) \
  in consensus by giving weight to votes and proposals

### Why do I need to participate ?

👉 You increase chain security by :

* distributing the votes / proposals among more participants
* distributing the votes / proposals among more computer networks

### What is a participation key ?

👉 A secure voting only proxy for your account

* You generate a set of participation keys that will allow consensus (not gov) \
  voting on behalf of your account
* The amount of voting power is determined in real time based on the balance in your participating (online) account. You are free to use your Algo , **it is not locked**.
* A participation key is a actually a SET OF KEYS valid for specific round range only
* Participation nodes instantly forget/delete old keys used in voting for a specific round

### What is a participation node ?

👉 A computer running Algorand software with part. keys installed

* Any node can host part. keys and participate but non-archival, catchup node is the best
* Participation node needs  little resources - 2 CPU cores and 8 GB of RAM and SSD/NVMe disk
* :warning: Node needs stable Internet connection - otherwise it will not vote.
* :warning: Nodes need to run on diverse Internet networks so a single network outage does not cause significant vote loss. If you run on a free cloud tier then run on 3 different providers :smile:

### Can a node host multiple part. keys ?

👉 Yes

* There is no limit to number of participation keys a node can host
* You can host your own participation keys and/or keys of other community members

### Can many nodes host the same part. key  ?

👉Yes

* All nodes will issue votes and network will accept only first one safely ignoring duplicates
* This ensures an account still participates when one of your nodes goes down&#x20;

### Can relay nodes participate ?

👉Yes, but relay nodes are exposed to the Internet and this can, potentially, leak your keys. \
Not recommended for high stake accounts. Lost keys increase the chances of chain rollback by bad actors.

### Can I share my participation keys with a friend/pool/DeFi/node provider ?

👉Yes, as long as you trust the proxy.

### I want to participate but don't want to run a node

👉Share your participation key.

* Ask your friend run a node for you
* Buy a service that does that for you (TBA)

### What hardware do I need to run a participation node

👉minimal: 2x vCPU, 4GB RAM , 20GB SSD/NVMe, 1TB monthly &#x20;

👉optimal: 4x vCPU, 8GB RAM , 20GB SSD/NVMe, 1TB monthly &#x20;

* Current traffic is low, you can use low-end physical machine or virtual machines
* You can use "shared CPU" or "burstable 12.5% CPU" machines to save on costs

{% hint style="info" %}
Participation nodes need to run on diversified networks to prevent mass outages. \
Running a free cloud or ultra cheap instance ? Try running at least two on different continents and install the same participation key on both machines :D
{% endhint %}
