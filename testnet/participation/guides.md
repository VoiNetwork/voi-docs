# Guides

### What are HW requirements for a node ?

👉minimal: 2x vCPU, 4GB RAM , 20GB SSD/NVMe, 1TB monthly &#x20;

👉optimal: 4x vCPU, 8GB RAM , 20GB SSD/NVMe, 1TB monthly &#x20;

* Current traffic is low, you can use low-end physical machine or virtual machines
* You can use "shared CPU" or "burstable 12.5% CPU" machines to save on costs

### Where to host my node ?

{% hint style="info" %}
Participation nodes need to run on diversified networks to prevent mass outages. \
Running a free cloud or ultra cheap instance ? Try running at least two on different continents and install the same participation key on both machines :D
{% endhint %}

### How to participate ?

* Choose a place to run your node - or better yet - choose two :)
* Follow any guide from the [node running section](../node-running/)
*   Add you account to the wallet\


    ```
    goal wallet new VoiParticipation
    goal account import
    ```
*   Generate participation keys and mark your account as online, setting `roundFirstValid`  to current round and `roundLastValid` to current round + 3000000\


    ```bash
    goal account addpartkey --roundFirstValid 0 --roundLastValid 3000000
    ```
