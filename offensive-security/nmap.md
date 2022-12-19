---
description: >-
  These are my go-to nmap commands. I usually start with a quick scan of the top
  ports and then figure out where to go from there.
---

# Nmap

### Commands Table

#### General Commands

| Usage                       | Command              |
| --------------------------- | -------------------- |
| List Scan                   | -sL                  |
| Ping Scan                   | -sp                  |
| No Port Scan                | -Pn                  |
| Stealth Scan (Very Useful)  | -sS                  |
| All Ports                   | -p-                  |
| Given Ports                 | -p 443,80,22         |
| TCP Scan                    | -sT                  |
| TCP SYN Ping                | -PS                  |
| TCP ACK Ping                | -PA                  |
| UDP Scan                    | -sU                  |
| UDP Ping                    | -PU                  |
| Version Detection           | -sV                  |
| OS Detection                | -O                   |
| Host Discovery              | -sP                  |
| --top-ports NUMBER (ex 25)  | --top-ports 25       |
| OS Detection (Guessing)     | --osscan-guess       |
| Disable Arp Ping            | `--disable-arp-ping` |
| Only Show Open Ports        | --open               |
| Reason for the port state   | --reason             |
| Traceroute                  | --traceroute         |
| Aggressive Scan             | -A                   |
| Verbose Mode                | -v or -vv or -v3     |

#### Bypassing IPS/IDS (firewall)

| Usage                                    | Command          |
| ---------------------------------------- | ---------------- |
| Spoof Source Address                     | -S               |
| Using Known Ports s Source Port          | --source-port    |
| Spoof Mac Address                        | --spoof-mac      |
| Randomize Scanning Order                 | --randomize-host |
| Send Packets with Bogus TCP/UDP Checksum | --badsum         |
| Null Scan                                | -sN              |

#### Timing

| Usage                                   | Command    |
| --------------------------------------- | ---------- |
| Timing Option                           | -T(option) |
| Paranoid - 5 min delay between requests | -T0        |
| Sneaky - 15 Sec delay                   | -T1        |
| Polite - 0.4 Sec delay                  | -T2        |
| Default - Parallel Scan                 | -T3        |
| Aggressive - Fast                       | -T4        |
| Insane - Just use it on yourself        | -T5        |

NOTE: It should be noted that -T3 is the default timing mode for nmap and is generally sufficient for most purposes. However, I personally use -T4 for CTFs as it is faster and -T2 for sensitive clients.

#### Saving Results

| Usage                            | Command                                    |
| -------------------------------- | ------------------------------------------ |
| Saves what you see on the screen | -oN (location)/(filename).(file extention) |
| Grepable                         | -oG (location)/(filename).(file extention) |
| XML                              | -oX (location)/(filename).(file extention) |
| Save in all formats              | -oA (location)/                            |

NOTE: I typically use the -oN option in conjunction with the -vv option for verbose mode, or I pipe the output into a text file. On occasion, I use grep to filter the output, although I prefer to save all the details and filter through them at a later time.

#### My Commands

I usually start with this command as it is giving me an idea of what kind of configuration I am dealing with.

```
sudo nmap -Pn -sS --top-ports 25 IP_ADDRESS/RANGE --open -vv > results.txt
```

If I couldn't find anything, I'll use this command

```
sudo nmap -Pn -sT -p- IP_ADDRESS/RANGE -T2 --open --reason -vv > results.txt
```

I then use the below command for OS detection

```
sudo nmap -Pn -sS -O IP_ADDRESS/RANGE -T2 --open -vv> OS_results.txt
```

Then I'll do a Vulnerability scan on the open ports

```
sudo nmap -Pn -p PORT --vuln script IP_ADDRESS -vv > vuln_results.txt
```
