---
title: "Linux"
linkTitle: "Linux"
weight: 20
menu:
  main:
    weight: 20
---

## Debugging Bash Scripts

```bash
#! /bin/bash -x
```
* outputs everything from the script
* `set -x` to enable debugging at a certain spot and `set +x` to the end

## Clear ZSH history

1. Open `.zsh_history`
1. Delete the lines you want removed and save the file
1. Restart your terminal

## Useful Commands

###  Force a Password Change

```bash
chage -d 0 <user>
```

### Redhat/CentOS/Oracle Linux Version

```bash
cat /etc/redhat-release
cat /etc/oracle-release
```

### Get All Installed Linux Kernels

```bash
uname -a
```

### Get VM Serial Number

```bash
sudo dmidecode -t system | grep Serial
```

### Force Reboot Host
> systemd hosts that aren't responding

```bash
sudo systemctl --force --force reboot
```

### Run logrotate Manually

```bash
/usr/sbin/logrotate /etc/logrotate.conf
```
