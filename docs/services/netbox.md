# Netbox

SOWN uses [Netbox](https://github.com/netbox-community/netbox) to record information about our servers and infrastructure. It provides both Data Center Infrastructure Management (DCIM) and IP Address Management (IPAM) sources of truth which are then used by other systems to drive automation.

If you are looking for more information about a VM, Server, IP Address, etc., Netbox is the correct place to look.

## Access

Our Netbox instance can be accessed at [netbox.sown.org.uk](https://netbox.sown.org.uk). If prompted for a password, select `OpenID Connect` to login with [SOWN SSO](./sso.md).

This service is publicly accessible, but requires authentication.

## Hosting

Netbox is hosted on it's own VM, aptly called [`netbox`](https://netbox.sown.org.uk/virtualization/virtual-machines/1/).

Netbox is installed at /opt/netbox and runs as the `netbox` user.

For upgrades, see netbox upgrade guide roughly:

```
cd /opt/netbox/
sudo -Hu netbox git fetch
sudo -Hu netbox git checkout vx.y.z
sudo -Hu netbox ./upgrade.sh
systemctl restart netbox netbox-rq
```