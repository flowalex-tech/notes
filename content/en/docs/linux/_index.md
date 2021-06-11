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

### Check for RedHat Packages

```bash
rpm -qa --queryformat="%{NAME}-%{VERSION}-%{RELEASE}.%{ARCH} - %{VENDOR}\n" | grep "Red Hat"
```
### Swap

#### Disable Swap
```bash
swapoff
```
#### Enable Swap
```bash
swapon
```
## Logical Volume Management

### Creating a Filesystem (XFS)

```bash
lvcreate  -L <size> <LVname> <VG>
mkfs.xfs <path_to_LV>
mkdir -p <mount_point_location>
cp -p /etc/fstab /etc/fstab_<mount_point>
echo "<filesystem_path> <location_of_mount_point> xfs defaults,nofail 0 0" >> /etc/fstab
systemctl daemon-reload
mount <filesystem_mount_point>
```
### Expanding a Filesystem

#### XFS
1. Extend the logical volume
```bash
lvextend -L +<size_to_add> <logical_volume>
lvextend -L <expected_size> <logical_volume>
```
2. Resize filesystem to fill logical volume
```bash
xfs_growfs <mount_point>
```
#### EXT
```bash
lvextend -L +<size_to_add> <logical_volume>
lvextend -L <expected_size> <logical_volume>
```
### Repair XFS Filesystem
1. Unmount Filesystem
```bash
umount <fs_mount_point>
```
2. Run XFS_repair
```bash
xfs_repair <full_path_of_logical_volume>
```
### Physical Volume
> Create a volume
```bash
pvcreate <device_name>
```
### Volume Groups
#### VGCreate
```bash
vgcreate -cn <vgname> <disk_path> <disk_path...>
```
#### VGExtend
```bash
vgextend <device_name_of_VG> <device_name_of_PV>
```
#### VGReduce
```bash
vgreduce <device_name_of_VG> <device_name_of_PV>
```
### Logical Volumes
#### LVCreate
Option 1
```bash
lvcreate -L <size> -n <name_of_LV> <VG_name>
```
Option 2
```bash
lvcreate -l <number_of_extents> -n <name_of_LV> <VG_name>
```
#### LVExtend
```bash
lvextend -L +<size_to_add> <logical_volume>
lvextend -L <expected_size> <logical_volume>
```
#### LVRemove
```bash
lvremove <LS_path>
```

## LDAP

### Delete from ldap

```bash
ldapdelete -x -h <domain_controller> 'CN=<SERVER>,OU=<OU1>,OU=<OU2>,DC=example,DC=com' -D '<user_account> -w <user_password>
```

### Net ADs Commands

#### Join
```bash
netads join -U 'user_account%password'
```
#### Leave

```bash
netads leave -U 'user_account%password'
```

### Keytab Count
```bash
klist -t -k /etc/krb5.keytab | wc -l
```

## Find Large files

```bash
find <dir> -xdev -type f -size 40000 -exec ls -hl {} \; | sort -n -k 5
```
