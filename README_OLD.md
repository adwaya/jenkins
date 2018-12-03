![](/jenkins-logo.png)
#Installation on Ubuntu :+1:
- Create a Ubuntu VM and login to the server
- Run `apt-get update`and wait for it to get completed
- Run `wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -` to add the key and this should return `OK`
- Then Run `sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'` , this command will add the *URL* to the sources list.
- Then do an `apt-get update`, 
- [Optional]The above might throw error depends on your infrastructure and when you get an error which says `Signature by key 36E47E1CC4DRR5E8152D115PP0B5E0AB11FD4949 uses weak digest algorithm (SHA1)` please follow the below step
```
apt list --upgradable
Listing... Done
apt/xenial-updates,xenial-security 1.2.15ubuntu0.2 amd64 [upgradable from: 1.2.15]
apt-transport-https/xenial-updates,xenial-security 1.2.15ubuntu0.2 amd64 [upgradable from: 1.2.15]
apt-utils/xenial-updates,xenial-security 1.2.15ubuntu0.2 amd64 [upgradable from: 1.2.15]
bind9-host/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
dnsutils/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
grub-common/xenial-updates 2.02~beta2-36ubuntu3.6 amd64 [upgradable from: 2.02~beta2-36ubuntu3.2]
grub-pc/xenial-updates 2.02~beta2-36ubuntu3.6 amd64 [upgradable from: 2.02~beta2-36ubuntu3.2]
grub-pc-bin/xenial-updates 2.02~beta2-36ubuntu3.6 amd64 [upgradable from: 2.02~beta2-36ubuntu3.2]
grub2-common/xenial-updates 2.02~beta2-36ubuntu3.6 amd64 [upgradable from: 2.02~beta2-36ubuntu3.2]
ifupdown/xenial-updates 0.8.10ubuntu1.2 amd64 [upgradable from: 0.8.10ubuntu1.1]

```
- In such case do an `apt-get upgrade` & wait for it to complete
- Now install jenkins using `apt-get install jenkins` and wait till it gets completed with,
```
...
Setting up jenkins (2.32.1) ...
insserv: warning: script 'mcollective' missing LSB tags and overrides
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for systemd (229-4ubuntu13) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for ca-certificates (20160104ubuntu1) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
done.
```
- Check the installation of jenkins using `service jenkins status` and see the below output
```
● jenkins.service - LSB: Start Jenkins at boot time
   Loaded: loaded (/etc/init.d/jenkins; bad; vendor preset: enabled)
   Active: active (exited) since Wed 2017-01-04 11:51:58 UTC; 1min 21s ago
     Docs: man:systemd-sysv-generator(8)
```
- Also double check jenkins working via 
```
 ps -ef |grep jenkins
jenkins  32986     1  0 11:51 ?        00:00:00 /lib/systemd/systemd --user
jenkins  32987 32986  0 11:51 ?        00:00:00 (sd-pam)
jenkins  32997     1  0 11:51 ?        00:00:00 /usr/bin/daemon --name=jenkins --inherit --env=JENKINS_HOME=/var/lib/jenkins --output=/var/log/jenkins/jenkins.log --pidfile=/var/run/jenkins/jenkins.pid -- /usr/bin/java -Djava.awt.headless=true -jar /usr/share/jenkins/jenkins.war --webroot=/var/cache/jenkins/war --httpPort=8080
jenkins  32998 32997 11 11:51 ?        00:00:17 /usr/bin/java -Djava.awt.headless=true -jar /usr/share/jenkins/jenkins.war --webroot=/var/cache/jenkins/war --httpPort=8080
root     34095  6741  0 11:54 pts/0    00:00:00 grep --color=auto jenkins
```
- Check the application via the URL `<hostname?:8080` and find the below UI ![](/img/ui-jenkins.JPG)
- The above screen needs an **administator** password to unlock the jenkins and normally this will be stored under the location mentioned `/var/lib/jenkins/secrets/initialAdminPassword`
- CopyPaste the password `efe635a7840d437e6339658f2b9656c0` and proceed
- If your face an error says Offline ![](/img/proxy-jenkins.JPG), it is a proxy issue and add proxy to jenkins application and proceed
- Then `Install Suggested Plugins` and wait for it to complete then proceed with admin user `Continue as admin`
- Finally your jenkins UI is up and runnnig when you say `Start using Jenkins` ![](/img/jenkins-final-ui.JPG)
- Start Playing with Jenkins :+1:



