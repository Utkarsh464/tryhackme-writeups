# Firewall Fundamentals - Commands

## iptables Commands (Linux)

| Command | Description |
|---------|-------------|
| `iptables -L -v -n` | List all rules with packet/byte counts |
| `iptables -F` | Flush (delete) all rules |
| `iptables -P INPUT DROP` | Set default policy for INPUT chain to DROP |
| `iptables -P FORWARD DROP` | Set default policy for FORWARD chain to DROP |
| `iptables -P OUTPUT ACCEPT` | Set default policy for OUTPUT chain to ACCEPT |
| `iptables -A INPUT -s 10.0.0.0/24 -j ACCEPT` | Allow traffic from internal subnet |
| `iptables -A INPUT -p tcp --dport 22 -j ACCEPT` | Allow SSH (port 22) inbound |
| `iptables -A INPUT -p tcp --dport 80 -j ACCEPT` | Allow HTTP (port 80) inbound |
| `iptables -A INPUT -p tcp --dport 443 -j ACCEPT` | Allow HTTPS (port 443) inbound |
| `iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT` | Allow established connections |
| `iptables -A INPUT -s 10.10.10.10 -j DROP` | Block traffic from a specific IP |
| `iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport 80 -j ACCEPT` | Forward HTTP traffic between interfaces |
| `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE` | Source NAT for internet access |
| `iptables -t nat -A PREROUTING -p tcp --dport 8080 -j DNAT --to-destination 10.0.0.5:80` | Port forwarding to internal server |
| `iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT` | Rate limit ICMP (ping) |
| `iptables -A INPUT -j LOG --log-prefix "FW-DROP: "` | Log dropped packets |
| `iptables-save > /etc/iptables/rules.v4` | Save rules to persist across reboot |

## nftables Commands (Modern Linux)

| Command | Description |
|---------|-------------|
| `nft list ruleset` | List all nftables rules |
| `nft add table inet filter` | Create a new table |
| `nft add chain inet filter input { type filter hook input priority 0\; }` | Add INPUT chain |
| `nft add rule inet filter input tcp dport 22 accept` | Allow SSH |
| `nft add rule inet filter input ip saddr 10.0.0.0/24 accept` | Allow internal subnet |
| `nft add rule inet filter input drop` | Default drop |

## Windows Firewall Commands

| Command | Description |
|---------|-------------|
| `netsh advfirewall show allprofiles` | Show firewall status for all profiles |
| `netsh advfirewall set allprofiles state on` | Enable firewall for all profiles |
| `netsh advfirewall set allprofiles state off` | Disable firewall for all profiles |
| `netsh advfirewall firewall add rule name="Allow HTTP" dir=in action=allow protocol=TCP localport=80` | Allow inbound HTTP |
| `netsh advfirewall firewall add rule name="Block IP" dir=in action=block remoteip=10.10.10.10` | Block inbound from an IP |
| `netsh advfirewall firewall show rule name=all verbose` | Show all firewall rules with details |
| `netsh advfirewall firewall delete rule name="Allow HTTP"` | Delete a specific rule |
| `netsh advfirewall export "C:\backup.wfw"` | Export firewall policy |
| `netsh advfirewall import "C:\backup.wfw"` | Import firewall policy |

## pfSense / OPNsense (Reference)

| Command | Description |
|---------|-------------|
| `pfctl -s rules` | List packet filter rules |
| `pfctl -s state` | List state table entries |
| `pfctl -s info` | Show pf statistics |
| `pfctl -s all` | Show all pf information |
| `tcpdump -i pflog0` | Monitor firewall log |
