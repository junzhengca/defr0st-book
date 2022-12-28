---
description: Tips and tricks for Linux Privilege Escalation
---

# Linux PrivEsc

## Things to Check

Before proceeding further, it is always a good idea to just poke around the system to see what we can do.

### List sudo permissions

Running `sudo -l` should tell you what command current user can run as `root`.

```shell
sudo -l

# Output (in this example, kali is sudoer):
# Matching Defaults entries for kali on kali:
#    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty
# 
# User kali may run the following commands on kali:
#     (ALL : ALL) ALL
```

## Interesting Binaries

There are some programs that's quite interesting and worth a look to see if you can exploit them.

[dstat.md](linux-privesc/dstat.md "mention")



