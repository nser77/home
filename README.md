# home
Overview of my personal infrastructure.

<p align="center">
  <img src="data/network.png" alt="network"/>
</p>

## OVH
Main VPS data center.
Running minimal services and mainly used as entry-point or vpn-agregator.

### Ubuntu
Machine mainly used as Firewall - with SHOREWALL - and as VPN-Agregator - with WIREGUARD - to manage backbone network. 
Performing NAT (MASQ, 1:1), policies and security controls.

Running a DNS service to manage backbone's domain names and dns-leak for vpn's users.

Can also run front-end applications.

## DC-ITA
Located in Italy, running backend services and secured with MIKROTIK.

```
N*2 MIKROTIK Router
N*2 MIKROTIK Access Point
N*1 ZYXEL Managed Switch
N*2 Pine64 (ROCK64 and Pine64)
```

### MIKROTIK
Post-Quantum WIREGUARD peer that interconnect DC-ITA with OVH.

Managing only one PPPoE interface with one Public IP, two MIKROIKs and VRRP (on/off switch script on MIKROTIK); alse running VRRP on LAN interfaces to serve local infrastructure.

Managing local "family" network with CAPsMAN (2 APs), VLAN (access and trunk mode) and security policies.

### Ubuntu cluster
Running backend services clustered with Keepalived (keepalived.org).

Some examples could be: CockroachDB, Elastic Search or even REDIS.

## DC-ES
Located in Spain, running backend services and still not secured with MIKROTIK.

```
N*1 RASPERRY PI
```

### Ubuntu stand-alone
Post-Quantum WIREGUARD peer that serve out backend services.

# VPN and Public IP
Some VPN actors are also able to use the infrastructure to masquerade their IP (thanks to kernel ip forwarding!).
