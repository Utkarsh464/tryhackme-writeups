# ipconfig

## Syntax
`ipconfig [options]`

## Purpose
Windows command to display and manage network interface configuration (IP addresses, DNS, DHCP status).

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `/all` | Show full configuration (MAC, DNS, DHCP) |
| `/release` | Release DHCP lease |
| `/renew` | Renew DHCP lease |
| `/flushdns` | Clear DNS cache |
| `/displaydns` | Show DNS resolver cache |
| `/registerdns` | Refresh DNS registration |
| `/showclassid` | Show DHCP class ID |
| `/setclassid` | Set DHCP class ID |

## Examples
```cmd
ipconfig
ipconfig /all
ipconfig /flushdns
ipconfig /release && ipconfig /renew
```

## Compatibility
Windows