# oneliners
*Useful unix one-liners – Battle Tested in production :fire:*

## Linux commands

### pgrep
Kill all Java processes running under Hadoop user whose parent died.
```
$ pgrep -P 1 -u hadoop java | xargs kill -TERM
```
Standard `ps -F --ppid 1 -C java -u hadoop` won't work in that case since it does **OR** filtering but but **AND**.
