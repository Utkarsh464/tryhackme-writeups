# systemctl

## Syntax
`systemctl [command] [unit]`

## Purpose
Controls the systemd service manager — starts, stops, enables, disables, and checks status of services.

## Common Parameters

| Subcommand | Description |
|-----------|-------------|
| `start` | Start a service |
| `stop` | Stop a service |
| `restart` | Restart a service |
| `reload` | Reload config without stopping |
| `status` | Show service status and recent logs |
| `enable` | Start at boot |
| `disable` | Don't start at boot |
| `is-active` | Check if running |
| `is-enabled` | Check if enabled at boot |
| `list-units` | List loaded service units |
| `--type=service` | Filter by service type |
| `--state=running` | Filter by state |

## Examples
```bash
systemctl status apache2
systemctl start nginx
systemctl enable ssh
systemctl list-units --type=service --state=running
systemctl reload ufw
```

## Compatibility
Linux