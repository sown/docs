# DNS

We have three way split DNS - an external zone that's visible to the world, a university-internal zone that's only visible inside the university network, and a SOWN-internal zone that's only visible inside SOWN.

## External and universiversity-internal DNS

Our domains `suws.org.uk` and `sown.org.uk` both have DNS hosted by the University, with DNS managed through their Infoblox system. Certain SOWN members have access to the web interface to update the records.

The university-internal zone is also managed through this.

## SOWN Internal DNS

Our internal DNS for `sown.org.uk` is hosted on our legacy server `auth2` running BIND. This also hosts reverse DNS for `10.5.0.0/16` and `2001:630:d0:f700::/56`. The DNS zone is built hourly by `/etc/cron.hourly/updatednszones`.

Parts of the zones are built from the legacy admin system, `node_control`, which is invoked through a PHP script and writes out temporary zonefiles. This is what generates the DNS records used for our nodes.

These are combined with newer parts of the zonefile generated from Netbox. This uses netbox export templates which generate the zonefile. This is what generates the DNS records for our servers and infrastructure.

The script then concatenates the zonefiles together, so the final zone is the combination of these two.

## Resolvers
Servers within SOWN should use our floating gateway addresses (`10.5.0.254` and `2001:630:d0:f700::254`) as DNS resolvers. These run BIND, and also hold our internal zones, AXFR'd from auth2. This means our internal DNS still works when auth2 is down.
