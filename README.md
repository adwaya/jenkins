
## Installing on **Ubuntu 18.04**

- First, add the repository key to the system: `wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -`
- Next, append the Debian package repository address to the server's `sources.list` using `sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'`
- Run `update` so that `apt` will use the new repository : `sudo apt update`
- Java 8 is needed : `apt-get install openjdk-8-jdk`
- Finally, install Jenkins and its dependencies : `sudo apt install jenkins`
- Let's start Jenkins using `systemctl start jenkins`
- Access Jenkins WebUI using `<IPAddress>:8080` on the browser
