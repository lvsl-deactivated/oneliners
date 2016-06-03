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

## Linux tools
### ack
[Ack](http://beyondgrep.com/) is awesome, single file in Perl (~4K lines).
Find all files under current dir with that name:
```
$ ack -g bazinga.jpg
```

Find imports of some `legacy_crap` in huge Python codebase:
```
$ ack --python '.*import.*legacy_crap.*'
```

### fzf
[Ffz](https://github.com/junegunn/fzf-bin/releases) is a fuzzy directory search. Useful for working with huge code repo,
like in most companies. Installs as a stand-alone binary with zere depedencies.
In a huge repository it's really useful to have the following shell alias: `alias vzv="f=$(fzf) && vim $f"`. Using it you can always start from a root of a huge repo and avoid cd-ing into directories and hintting <TAB> a lot.

