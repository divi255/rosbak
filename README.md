# Mikrotik RouterOS backup tool

## Instalation

```shell
pip3 install rosbak
```

## What is rosbak

**rosbak** is a Python command line tool which allows backup Mikrotik RouterOS
routers and switches.

Keeping backup files inside RouterOS is usually unsafe, as when the equipment
fail, you have no access to them.

**rosbak** performs RouterOS backup and copies files to the specified location.

# Requirements

* RouterOS >= 6.45, as **rosbak** uses scp
* RouterOS ssh service should be turned on
* You should have an access to RouterOS host

## Usage

```shell
rosbak [options] <host>
```

e.g.

```
rosbak -d /backups router1
```

## Configuration

You may put configuration to */usr/local/etc/rosbak.yml*

Configuration contains global variable *dir* which points to default backup
location (you may use {host} param e.g. /backups/{host}, in this case backups
are stored e.g. to */backups/router1*)

Host sections in configuration file may contain router IP (*addr*), port,
backup *delay*, etc.

Configuration file is optional.

## Why backup delay

RouterOS performs backups in background. Backup delay param is required to ask
**rosbak** wait the specified number of seconds before copying backup.

## Export

Command line param *-x* or *export: true* in host configuration tells
**rosbak** to perform configuration export as well (*/export file=...*)

Configuration exports are useful when you need to restore backup partially,
manually copying settings one-by-one (e.g. when restoring it on the another
model).

## Copyright and warranty

**rosbak** is provided as-is under MIT license. **rosbak** is a 3rd party tool
and is not affiliated with SIA Mikrotīkls.
