```
iptables -t nat -A PREROUTING -i wg0 -d 10.11.33.0/24 -j NETMAP --to 10.12.34.0/24
iptables -t nat -A POSTROUTING -o wg0 -d 10.12.34.0/24 -j NETMAP --to 10.11.33.0/24
iptables -A FORWARD -i wg0 -o tun0 -j ACCEPT
iptables -A FORWARD -i tun0 -o wg0 -j ACCEPT
```
