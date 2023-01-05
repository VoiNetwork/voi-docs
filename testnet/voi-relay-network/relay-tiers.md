# Relay tiers

### Relay network tiers

Voi testnet network has a two tier structure&#x20;

#### Tier 1 : Light relays

Light relays run modified algorand code that allows non-archival mode with redirect to archival tier for older blocks / catchpoints.&#x20;

Minimum hardware requirements depend on the average transaction volume

{% tabs %}
{% tab title="up to 50 TPS" %}
generic Virtual Machine with 1TB monthly traffic

* 2 vCPU
* 4GB RAM
* 20GB Local SSD/NVMe or SSD Cloud volume
{% endtab %}

{% tab title="up to 200 TPS" %}
generic Virtual Machine with 10 TB monthly traffic

* 4 vCPU
* 8 GB RAM
* 20GB Local SSD/NVMe \


{% hint style="warning" %}
SSD Cloud volume might be insufficient&#x20;
{% endhint %}
{% endtab %}

{% tab title="up to 1000 TPS" %}
generic Virtual Machine with 40 TB monthly traffic

* 8 vCPU
* 12GB RAM
* 40GB Local SSD/NVMe&#x20;

{% hint style="danger" %}
Cloud volume not supported
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
* Do not host your participation keys on relays. Participation keys should be protected against theft (to prevent rollback) and against data loss (to maintain consensus)
* Host relays on stable Internet (< 1 hr downtime annually) to maintain consensus
* Pick a network provider that is not on the list at the bottom or one that hosts least nodes - to maintain consensus during global network outages
{% endhint %}

#### Tier 2 : Archival relays

This tier runs on heavy duty servers that store the whole blockchain history starting from genesis block. Archival relays allow new nodes to connect to the network either in archival or catch-up mode.&#x20;

### Relay network bootstrap SRV entries

{% tabs %}
{% tab title="Light relay tier" %}
```json
dig +short srv _algobootstrap._tcp.voi-test.voi.network
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
{% endtab %}

{% tab title="Archival tier" %}
```bash
dig +short srv _archive._tcp.voi-test.voi.network
1 1 8080 a-co00.test.voi.network.
1 1 8080 a-co01.test.voi.network.
1 1 8080 a-co02.test.voi.network.
```
{% endtab %}
{% endtabs %}

### Relay network decentralization stats

{% tabs %}
{% tab title="Light relay tier" %}
| Network    | Relays |
| ---------- | ------ |
| Oracle     | 5      |
| Hetzner    | 2      |
| SpeedyPage | 2      |

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Archival tier" %}
| Network    | Archival relays |
| ---------- | --------------- |
| Oracle     | 1               |
| Hetzner    | 1               |
| SpeedyPage | 1               |
{% endtab %}
{% endtabs %}

###

