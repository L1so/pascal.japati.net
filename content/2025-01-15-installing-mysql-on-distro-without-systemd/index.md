---
title: Installing MySQL on distro without systemd
date: 2025-01-15
taxonomies:
  tags: [linux, tech]
---
I'm using MX Linux, distro derived from Debian—the latest version is using Debian 12 Bookworm, I have been using it for around 2 years and have done great job assisting my everyday need, everything here is stable.

### Absence of systemd
For a newcomer or refuge that came from Ubuntu world, there might be a problem migrating to this distro, by default, MX Linux does not offer systemd init system, rather it is still using traditional sysVinit. Here is the comparison of those two init system (taken from https://blog.desdelinux.net/id/systemd-versus-sysvinit-systemd-shim/)
![](Pasted%20image%2020250115141200.png)
### Installing MySQL on MX Linux
Modern MySQL (I think 5.7 and above) uses systemd to handle their service file—the absence of systemd has led me to searching the internet to look for workaround, as MySQL refuses to work without systemd installed, it will failed to launch.

To overcome this problem, you need to grab mysql init script and place it on `/etc/init.d/mysql`.
```
$ sudo wget -O /etc/init.d/mysql 'https://gist.githubusercontent.com/L1so/f79e5e265c5881da7d2983c2070894e4/raw/44d789277369f3e3a056c4078a38ae96c5dd0f80/mysql-init-d.sh'
$ sudo chmod 755 /etc/init.d/mysql
$ sudo /etc/init.d/mysql start
```

After this you should be able to start and stop MySQL as follows:

```
sudo service mysql start
sudo service mysql stop
```
Cheers !