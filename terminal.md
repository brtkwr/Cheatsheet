# Terminal

## `git` reset remote a previous commit

``` bash
$ git log # and copy the commit hash
$ git reset --hard <paste commit hash>
$ git push -f origin master
```

## `svn` checkout a repository

``` bash
$ svn co svn://svn.repository.com/
```

## Continously monitor a file

``` bash
$ sudo tail -n 100 -f /var/log/syslog | grep CRON
```

## Running docker without `sudo` on Ubuntu 16.04

``` bash
$ sudo groupadd docker
$ sudo usermod -aG docker $USER
$ sudo service docker restart
$ newgrp docker
$ docker ps
```

## Backing up minutely, hourly, daily and weekly using `crontab`:

First launch `crontab -e` on `bash` and add the following to the bottom of the file:

``` bash
# Backup files minutely, hourly, daily, weekly
# m h  dom mon dow   command
*/3 * * * * rsync -arzv --no-o --no-g /home/user.name/ /home/user.name/Backup/0Minutely/ --delete
0 * * * * rsync -arzv --no-o --no-g /home/user.name/ /home/user.name/Backup/1Hourly/ --delete
0 20 * * * rsync -arzv --no-o --no-g /home/user.name/ /home/user.name/Backup/2Daily/ --delete
0 20 * * 5 rsync -arzv --no-o --no-g /home/user.name/ /home/user.name/Backup/3Weekly/ --delete
```

Press `Control + X` followed by `Yes` and `Enter` to save.

## Periodically force physical linkage between files using `crontab`

First launch `crontab -e` on `bash` and add the following to the bottom of the file:

``` bash
# m h  dom mon dow   command
* * * * * ln -Pf ~/Desktop/MyFolder.bib ~/Documents/report/bibliography.bib
```

Press `Control + X` followed by `Yes` and `Enter` to save.

## Running command on terminal

``` bash
$ A; B    # Run A and then B, regardless of success of A
$ A && B  # Run B if A succeeded
$ A || B  # Run B if A failed
$ A &     # Run A in background.
```