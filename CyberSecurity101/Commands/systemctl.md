# systemctl

**System Control** — the command-line interface for `systemd`, the init system and service manager used by most modern Linux distributions.

## Syntax

```
systemctl <command> [unit...]
```

## Purpose

Manage systemd services, check service status, enable/disable services at boot, and control system state. The standard tool for service management on Debian/Ubuntu (since 15.04), RHEL/CentOS (since 7), Arch Linux, and most other modern Linux distributions.

## Common Commands

| Command | Description |
|---------|-------------|
| `start <unit>` | Start a service |
| `stop <unit>` | Stop a service |
| `restart <unit>` | Restart a service |
| `reload <unit>` | Reload configuration without stopping |
| `enable <unit>` | Enable service to start at boot |
| `disable <unit>` | Disable service from starting at boot |
| `status <unit>` | Show service status (running, enabled, recent logs) |
| `is-active <unit>` | Check if service is running |
| `is-enabled <unit>` | Check if service is enabled |
| `list-units` | List active units |
| `list-unit-files` | List all unit files (enabled/disabled/static) |
| `daemon-reload` | Reload systemd manager configuration |
| `mask <unit>` | Prevent a service from being started |
| `unmask <unit>` | Unmask a previously masked service |

## Unit Types

| Type | Extension | Example |
|------|-----------|---------|
| Service | `.service` | `nginx.service` |
| Timer | `.timer` | `daily-cleanup.timer` |
| Socket | `.socket` | `sshd.socket` |
| Mount | `.mount` | `home.mount` |
| Target | `.target` | `multi-user.target` (like runlevel 3) |

## Examples

```bash
# Check service status
systemctl status nginx

# Start and enable a service at boot
sudo systemctl enable --now nginx

# Stop a service
sudo systemctl stop apache2

# Restart with reload if supported
sudo systemctl reload-or-restart nginx

# List all running services
systemctl list-units --type=service --state=running

# List all failed services
systemctl --failed

# Enable a custom service unit
sudo systemctl enable /path/to/myapp.service

# Prevent a service from starting
sudo systemctl mask apache2

# Reload systemd after adding new unit files
sudo systemctl daemon-reload

# View service logs
journalctl -u nginx

# View boot time of services
systemd-analyze blame
```

## Common Mistakes

- Using `systemctl` without `sudo` — most systemctl commands require root privileges.
- Enabling without starting (`enable` vs `enable --now`) — `enable` only creates symlinks for boot, does not start the service immediately.
- Confusing `systemctl` with `service` — `service` is the legacy SysVinit command. Prefer `systemctl` on modern systems.
- Using `restart` when `reload` is sufficient — `reload` avoids downtime.
- Masking a service instead of disabling — masking creates a symlink to `/dev/null`, making the service impossible to start even manually.
- Not running `daemon-reload` after editing unit files — systemd caches unit files; changes take effect only after reload.

## Real-World Usage

- **Service management:** Start, stop, restart web servers (nginx, apache), databases (mysql, postgresql), and custom applications.
- **CTF privilege escalation:** Check for custom services running as root, exploit misconfigured systemd units.
- **Boot optimization:** Use `systemd-analyze blame` to identify slow-starting services.
- **Log inspection:** View service-specific logs with `journalctl -u <service>` for troubleshooting.
- **Security hardening:** Disable and mask unnecessary services to reduce attack surface.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full (systemd-based) | Debian 8+, Ubuntu 15.04+, RHEL 7+, Arch |
| Windows | N/A | Use `sc` or `Get-Service` |
| macOS | N/A | Use `launchctl` |

```bash
# systemctl is pre-installed on all systemd-based Linux distributions
```
