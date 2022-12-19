---
description: >-
  Fping is a useful tool for pinging that I find to be more efficient and
  reliable than nmap and the standard ping command.
---

# fping

While fping has many options, I usually only use three options

| Usage                  | Command |
| ---------------------- | ------- |
| Only Shows Alive Hosts | -a      |
| Generates Target List  | -g      |
| Quite Mode             | -q      |

There's only one command that I use and that is

```
fping -a -g -q 192.168.1.1/24 > pingresults.txt
```

NOTE: "> pingresults.txt" will save the results in a file called pingresults.txt in your current directory.
