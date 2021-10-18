# borgmatic-lvm-helper

## Installation
Install this python script to an executable path to be used by borgmatic (i.e. /usr/local/bin).
The command is used by two hooks ...

1. creating the snapshot before the backup will be started
2. removing the snapshot after the backup is finished

Please ensure you fit your location source directories to the snapshots.


## Configuration Example

```
location:
    # List of source directories to backup (required). Globs and tildes are expanded.
    source_directories:
        - /dev/raid1/borg_snapshot_mypartition

hooks:
    # List of one or more shell commands or scripts to execute before creating a
    # backup, run once per configuration file.
    before_backup:
        - lvm-helper create --lv /dev/raid1/mypartition -s 20

    after_backup:
        - lvm-helper remove --lv /dev/raid1/mypartition
```


