# Commands: Extending Your Network

## DHCP

| Command | Description |
|---------|-------------|
| `dhclient eth0` | Request a DHCP lease for an interface |
| `dhclient -r eth0` | Release the current DHCP lease |
| `cat /var/lib/dhcp/dhclient.leases` | View DHCP lease information |

## Routing

| Command | Description |
|---------|-------------|
| `ip route show` | Display the routing table |
| `ip route add default via 192.168.1.1` | Set the default gateway |
| `route -n` | Display the routing table (numeric) |

## Firewall / iptables

| Command | Description |
|---------|-------------|
| `sudo iptables -L` | List current iptables rules |
| `sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT` | Allow SSH inbound traffic |

## VPN

| Command | Description |
|---------|-------------|
| `sudo openvpn config.ovpn` | Connect to an OpenVPN server |
| `sudo killall openvpn` | Disconnect OpenVPN |
