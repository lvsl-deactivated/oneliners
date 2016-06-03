# oneliners
*Useful unix one-liners – Battle Tested in Production :fire:*

## Linux commands

### pgrep
Kill all Java processes running under Hadoop user whose parent died.
```
$ pgrep -P 1 -u hadoop java | xargs sudo kill -TERM
```
Standard `ps -F --ppid 1 -C java -u hadoop` won't work in that case since it does **OR** filtering but but **AND**.

### netstat, lsof
Find out what process is holding the port 2181:
```
sudo netstat -ap | grep 2181
```
or, looks less verbose:
```
sudo lsof -i :2181
```
