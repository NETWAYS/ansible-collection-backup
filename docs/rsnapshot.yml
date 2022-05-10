# Rsnapshot #

This simple roles installs `rsnapshot` and configures an hourly snapshot of common directories to a local volume.

## Variables ##

* `rsnapshot_snapshot_root`: Place to save backups. Will be created. (default: `/opt/backup/rsnapshot/`)
* `rsnapshot_timestamp_dir`: Directory to safe timestamps for backups. (default: `/root/rsnapshot/`)
* `rsnapshot_remote_snapshots`: Not implemented yet. (default: `false`)
* `rsnapshot_retains`: How many of which backup to keep. See below for details and defaults
* `rsnapshot_backups`: Which directory to backup. See below for details and defaults
* `rsnapshot_excludes`: What not to backup. See below for details and defaults

## Retains ##

Here's the default for this variable:

```
rsnapshot_retains:
  - name: hourly
    count: 24
    interval: hourly
    timestamp: true
  - name: daily
    count: 7
    interval: daily
  - name: weekly
    count: 4
    interval: weekly
  - name: monthly
    count: 12
    interval: monthly
  - name: yearly
    count: 10
    interval: yearly
```

Give a list of backup cycles and how many of each should be kept. The order is important and the more often they will be executed, the higher up in the list the entries should be.

You can activate `timestamp` as often as you want but with the way, `rsnapshot` works, only the one in the most frequent job will be accurate. This will update a file with the current timestamp immediately before running a backup. Due to the way, `rsnapshot` works this will help a lot with identifying when a backup was made.

## Backups ##

Here's the default:
```
rsnapshot_backups:
  - /root
  - /etc
  - /home
```

It's simply a list of directories to backup. In the current implementation no more options are available.

## Excludes ##

The default:
```
rsnapshot_excludes:
  - "*.sql"
```

A list of patterns, which files not to include in the backup.
