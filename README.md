# Edureka_Ansible
Action Items
•
•
•
•
Create separate roles for setting up Apache Tomcat and Apache Maven
Add the necessary logic to the roles to set up the tools
Create a new playbook and call Tomcat as well as Maven roles inside it
Execute the playbook on all the hosts
Commands to install Tomcat and Maven
Apache Tomcat:
1.
2.
3.
4.
5.
sudo apt-get update
sudo apt-get install default-jdk
sudo groupadd tomcat
sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
curl -O http://redrockdigimark.com/apachemirror/tomcat/tomcat-8/v8.5.31/bin/apache-
tomcat-8.5.31.tar.gz
6. sudo mkdir /opt/tomcat
7. sudo tar xzvf apache-tomcat-8*tar.gz -C /opt/tomcat --strip-components=1
8. sudo mkdir /opt/tomcat
9. cd /opt/tomcat
10. sudo chgrp -R tomcat /opt/tomcat
11. sudo chmod -R g+r conf
12. sudo chmod g+x conf
13. sudo chown -R tomcat webapps/ work/ temp/ logs/
14. Add this code to /etc/systemd/system/tomcat.service
[Unit]
Description=Apache Tomcat Web Application Container
After=network.targetd
[Service]
Type=forking
©Brain4ce Education Solutions Pvt. Ltd
Page 1Module 5: Configuration Management with Ansible
Environment=JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-amd64/jre
Environment=CATALINA_PID=/opt/tomcat/temp/tomcat.pid
Environment=CATALINA_HOME=/opt/tomcat
Environment=CATALINA_BASE=/opt/tomcat
Environment='CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC'
Environment='JAVA_OPTS=-Djava.awt.headless=true -
Djava.security.egd=file:/dev/./urandom'
ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh
User=tomcat
Group=tomcat
UMask=0007
RestartSec=10
Restart=always
[Install]
WantedBy=multi-user.target
15. sudo systemctl daemon-reload
16. sudo systemctl start tomcat
Apache Maven:
1.
2.
3.
4.
5.
sudo apt install -y python-software-properties
sudo add-apt-repository ppa:webupd8team/java
sudo apt update
sudo apt-get install default-jdk
cd /home/edureka/Downloads/ && wget
http://apache.mirror.digitalpacific.com.au/maven/maven-3/3.3.9/binaries/apache-
maven-3.3.9-bin.tar.gz
6. cd /opt/ && sudo tar -xzvf /home/edureka/Downloads/apache-maven-3.3.9-bin.tar.gz
7. sudo update-alternatives --install /usr/bin/mvn maven /opt/apache-maven-
3.3.9/bin/mvn 1001
