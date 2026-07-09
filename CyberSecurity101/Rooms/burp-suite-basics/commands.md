# Burp Suite: The Basics - Commands

## Burp Suite Keyboard Shortcuts

| Key Binding | Description |
|-------------|-------------|
| `Ctrl+Shift+T` | Open the Target tab |
| `Ctrl+Shift+P` | Open the Proxy tab |
| `Ctrl+Shift+R` | Open the Repeater tab |
| `Ctrl+Shift+I` | Open the Intruder tab |
| `Ctrl+Shift+D` | Open the Decoder tab |
| `Ctrl+Shift+E` | Open the Extender tab |
| `Ctrl+Shift+O` | Open the Options tab |
| `Ctrl+Shift+A` | Open the Alarm tab |
| `Ctrl+F` | Search within the current view |
| `Ctrl+I` | Toggle interception on/off |
| `Ctrl+Shift+B` | Send to Repeater |
| `Ctrl+Shift+I` (in Proxy) | Send to Intruder |
| `Forward` | Forward intercepted request/response |
| `Drop` | Drop intercepted request/response |
| `F5` | Refresh current view |

## Burp Suite Proxy Configuration

| Setting | Value |
|---------|-------|
| Proxy listener address | 127.0.0.1 |
| Proxy listener port | 8080 |
| Browser proxy HTTP | 127.0.0.1:8080 |
| Browser proxy SSL | 127.0.0.1:8080 |
| CA certificate download | http://burpsuite |
| CA certificate format | DER (.der) |

## Intruder Attack Types

| Attack Type | Payload Sets | Description |
|-------------|--------------|-------------|
| Sniper | 1 | Test each payload position with each value sequentially |
| Battering ram | 1 | Insert same payload into all positions simultaneously |
| Pitchfork | Multiple (same count) | Use corresponding payload values together |
| Cluster bomb | Multiple (all combinations) | Test every combination of all payload sets |

## Intruder Payload Types

| Payload Type | Description |
|--------------|-------------|
| Simple list | Manually defined list of strings |
| Runtime file | Load payloads from a file at runtime |
| Numbers | Sequential numbers with optional step, min, max |
| Brute forcer | Brute-force strings with specified character set and length |
| Custom iterator | Combine multiple payload lists with separators |
| Character substitution | Substitute characters with look-alikes (leet speak) |
| Case modification | Modify case of payload strings |
| Null payloads | Generate requests without payloads (for pacing) |
