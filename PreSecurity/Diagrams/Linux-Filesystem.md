# Linux Filesystem Hierarchy

```mermaid
graph TD
    Root[/] --> Bin[/bin]
    Root --> Sbin[/sbin]
    Root --> Etc[/etc]
    Root --> Home[/home]
    Root --> Var[/var]
    Root --> Tmp[/tmp]
    Root --> Dev[/dev]
    Root --> Proc[/proc]
    Root --> Usr[/usr]
    Root --> Opt[/opt]

    Home --> User1[user1/]
    Home --> User2[user2/]
    Var --> Log[/var/log]
    Var --> Spool[/var/spool]
    Var --> Cache[/var/cache]
    Etc --> Passwd[/etc/passwd]
    Etc --> Shadow[/etc/shadow]
    Etc --> Ssh[/etc/ssh/]
    Usr --> Local[/usr/local/]
    Bin --> Ls[ls, cp, mv, cat]
    Bin --> Bash[bash, sh]
```

The Linux filesystem follows the Filesystem Hierarchy Standard (FHS). Key directories include `/bin` (essential user binaries), `/etc` (configuration files), `/home` (user home directories), `/var` (variable data like logs), `/tmp` (temporary files), `/dev` (device files), and `/proc` (process and kernel information).
