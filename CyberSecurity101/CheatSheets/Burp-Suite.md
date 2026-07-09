# Burp Suite Cheat Sheet

## Proxy
| Action | Description |
|--------|-------------|
| `Proxy > Intercept ON` | Capture requests |
| `Proxy > Intercept OFF` | Pass-through |
| `Forward` | Send modified request |
| `Drop` | Discard request |
| `Action > Send to Repeater` | Ctrl+R |
| `Action > Send to Intruder` | Ctrl+I |
| `Action > Do an active scan` | Send to Scanner |
| `Action > Copy as curl` | Export to curl |
| `Action > Copy URL` | Copy full URL |
| `Action > Request in browser` | Get proxy URL for browser |
| `Proxy > Options` | Proxy settings (port, cert) |
| `Proxy > WebSockets History` | WS capture |
| `Proxy > HTTP History` | Browse captured traffic |

## Repeater
| Action | Description |
|--------|-------------|
| `Ctrl+R` | Send request to Repeater |
| `Send` | Send modified request |
| `Cancel` | Abort in-flight request |
| `<>` | Switch request/response view |
| `Render` | Render HTML response |
| `Pretty/Raw/Hex` | Content display modes |
| `Params` | View/modify parameters |
| `Headers` | View/modify headers |
| `Hex` | Edit raw bytes |
| `Copy as curl` | Export to curl |
| `Generate CSRF PoC` | Create CSRF proof |

## Intruder
| Action | Description |
|--------|-------------|
| `Ctrl+I` | Send to Intruder |
| `Positions > Clear §` | Clear payload positions |
| `Positions > Add §` | Mark as payload |
| `Positions > Auto` | Auto-detect positions |
| `Payloads > Payload set` | Choose set # |
| `Payloads > Simple list` | Manual list |
| `Payloads > Runtime file` | Load from file |
| `Payloads > Numbers` | Sequential numbers |
| `Payloads > Brute forcer` | Character brute |
| `Payloads > Case modification` | Case mutations |
| `Payloads > Add: prefix/suffix` | Modify payloads |
| `Options > Attack Results` | Matcher/grep |
| `Options > Grep-Extract` | Extract from response |
| `Options > Grep-Match` | Flag responses containing |
| `Attack type: Sniper` | One payload set, single position |
| `Attack type: Battering ram` | Same payload, all positions |
| `Attack type: Pitchfork` | Multiple sets, parallel |
| `Attack type: Cluster bomb` | Multiple sets, all combos |

## Scanner (Burp Pro)
| Feature | Description |
|---------|-------------|
| `Active Scan` | Active vulnerability scanning |
| `Passive Scan` | Passive (no requests sent) |
| `Crawl` | Discover URLs |
| `Live scan > Use suite scope` | Monitor scope |
| `Scan queue` | Manage scan tasks |
| `Scan config` | Customize scan settings |
| `Issue activity` | Vulnerability results |

## Decoder
| Feature | Description |
|---------|-------------|
| `Decode as...` | URL, HTML, Base64, Hex, ASCII |
| `Encode as...` | URL, HTML, Base64, Hex |
| `Hash` | MD5, SHA-1, SHA-256, etc. |
| `Smart decode` | Auto-detect encoding |
| `Hex dump` | Raw bytes view |
| `Text view` | Decoded text |

## Comparer
| Feature | Description |
|---------|-------------|
| `Select words` | Compare by words |
| `Select bytes` | Compare by bytes |
| `Compare results` | Side-by-side diff |
| `Sync views` | Scroll in sync |
| `Go to next/prev difference` | Navigate diff |

## Extensions (BApp Store)
| Extension | Purpose |
|-----------|---------|
| `JSON Beautifier` | Format JSON |
| `Logger++` | Advanced logging |
| `Turbo Intruder` | High-speed brute force |
| `Collaborator Everywhere` | OOB testing |
| `Autorize` | Auth/CORS testing |
| `Auth Analyzer` | Authentication analysis |
| `Upload Scanner` | File upload testing |
| `Param Miner` | Parameter discovery |
| `Backslash Powered Scanner` | De-sync attacks |

## Shortcuts
| Shortcut | Action |
|----------|--------|
| `Ctrl+R` | Send to Repeater |
| `Ctrl+I` | Send to Intruder |
| `Ctrl+Shift+R` | Send to Repeater (new tab) |
| `Ctrl+Shift+B` | Send to Intruder (positions) |
| `Ctrl+F` | Find |
| `Ctrl+G` | Go to line |
| `Ctrl+L` | Go to URL |
| `Ctrl+U` | URL decode |
| `Ctrl+Shift+U` | URL encode |
| `Ctrl+B` | Base64 decode |
| `Ctrl+Shift+B` | Base64 encode |
| `Ctrl+H` | HTTP history |
| `Ctrl+Shift+S` | Save item |

## Common Workflows
```bash
# 1. Configure browser proxy to 127.0.0.1:8080
# 2. Intercept OFF -> browse site -> Proxy > HTTP History
# 3. Right-click interesting requests -> Send to Intruder
# 4. Set payload positions with §
# 5. Add payload list
# 6. Start attack
# 7. Sort results by Length to find anomalies

# Parameter fuzzing
# 1. Send to Intruder
# 2. Mark parameter as position
# 3. Load wordlist (fuzzing, SecLists)
# 4. Compare response lengths

# Session handling
# Project options > Sessions > Session handling rules
# Add rule: Check session is valid (login request as macro)
```
