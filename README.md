What
====

This program tries to trace which process sends out what DNS queries.

Note that this is **NOT accurate**. Race conditions can happen and lead to wrong data.

Dependencies
====

* A recent Linux kernel (at least >= 4.1)
* Python >= 3.6
* [bcc (Python binding)](https://github.com/iovisor/bcc)
* [python-dnslib](https://bitbucket.org/paulc/dnslib)
* [python-netfilterqueue](https://github.com/lilydjwg/python-netfilterqueue)

Usage
====

Setup iptables:

```
sudo iptables -I OUTPUT -d 127.0.0.1 -p udp --dport 53 -j NFQUEUE --queue-num 2 --queue-bypass
```

Run it (Ctrl-C to stop):

```
sudo ./dnssnoop
```

Output fields:

```
TIME PID COMMAND_LINE DNS_QUESTION
```
