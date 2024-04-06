# Edureka_Ansible
Action Items <br>
Create separate roles for setting up Apache Tomcat and Apache Maven.
Add the necessary logic to the roles to set up the tools. <br>
Create a new playbook and call Tomcat as well as Maven roles inside it. <br>
Execute the playbook on all the hosts <br>
Commands to install Tomcat and Maven <br>
# Apache Tomcat:
sudo apt-get update <br>
sudo apt-get install default-jdk <br>
sudo groupadd tomcat <br>
sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat <br>
curl -O http://redrockdigimark.com/apachemirror/tomcat/tomcat-8/v8.5.31/bin/apache-tomcat-8.5.31.tar.gz <br>
sudo mkdir /opt/tomcat <br>
sudo tar xzvf apache-tomcat-8*tar.gz -C /opt/tomcat --strip-components=1 <br>
sudo mkdir /opt/tomcat <br>
cd /opt/tomcat <br>
sudo chgrp -R tomcat /opt/tomcat <br>
sudo chmod -R g+r conf <br>
sudo chmod g+x conf <br>
sudo chown -R tomcat webapps/ work/ temp/ logs/ <br>
# Add this code to /etc/systemd/system/tomcat.service
[Unit]
Description=Apache Tomcat Web Application Container <br>
After=network.targetd <br>
[Service] <br>
Type=forking <br>
©Brain4ce Education Solutions Pvt. Ltd <br>
Page 1Module 5: Configuration Management with Ansible <br>
Environment=JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-amd64/jre <br>
Environment=CATALINA_PID=/opt/tomcat/temp/tomcat.pid <br>
Environment=CATALINA_HOME=/opt/tomcat <br>
Environment=CATALINA_BASE=/opt/tomcat <br>
Environment='CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC' <br>
Environment='JAVA_OPTS=-Djava.awt.headless=true -Djava.security.egd=file:/dev/./urandom' <br>
ExecStart=/opt/tomcat/bin/startup.sh <br>
ExecStop=/opt/tomcat/bin/shutdown.sh <br>
User=tomcat <br>
Group=tomcat <br>
UMask=0007 <br>
RestartSec=10 <br>
Restart=always <br>
[Install] <br>
WantedBy=multi-user.target <br>
sudo systemctl daemon-reload <br>
sudo systemctl start tomcat <br>
# Apache Maven:
sudo apt install -y python-software-properties <br>
sudo add-apt-repository ppa:webupd8team/java <br>
sudo apt update <br>
sudo apt-get install default-jdk <br>
cd /home/edureka/Downloads/ && wget <br>
http://apache.mirror.digitalpacific.com.au/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz <br>
cd /opt/ && sudo tar -xzvf /home/edureka/Downloads/apache-maven-3.3.9-bin.tar.gz <br>
sudo update-alternatives --install /usr/bin/mvn maven /opt/apache-maven-3.3.9/bin/mvn 1001
