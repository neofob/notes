# Random notes on network
* Fix systemd-resolv


## Fix systemd-resolv
* Edit `/etc/systemd/resolved.conf`
```bash
# Enable DNS and domain for your LAN here
DNS=
Domains=
```
* Fix the symbolic link of `/etc/resolv.conf` to point to the right one
* `ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf`
* Restart service `service systemd-resolved restart`
*Now you should see your set DNS in /etc/resolv.conf*.
