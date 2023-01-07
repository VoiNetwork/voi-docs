# Diagnosing issues

### DNS LookupSRV / signature errors

:point\_right: Not an error, ignore or fix your local resolver settings

```json
{
  "file": "bootstrap.go",
  "function": "github.com/algorand/go-algorand/tools/network.ReadFromSRV",
  "level": "info",
  "line": 43,
  "msg": "ReadFromBootstrap: DNS LookupSRV failed when using system resolver: no signature in DNS response for _algobootstrap._tcp.voi-test.voi.network",
  "time": "2023-01-07T23:06:56.991692Z"
}
```

Your local DNS resolver is not configured to check for man-in-the-middle attacks on DNS but the node detects that and uses fallback resolver to make sure all is OK.\
\
To "fix" this :

*   add DNSSEC check to your `/etc/systemd/resolved.conf`&#x20;

    ```bash
    [Resolve]
    #... your current settings
    DNSSEC=allow-downgrade
    ```
* restart systemd-resolved \
  `systemctl restart systemd-resolved.service`
