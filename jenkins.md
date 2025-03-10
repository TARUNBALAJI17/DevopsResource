# Jenkins Installation Guide

## Prerequisites:
- **Java (JDK)**

### Step 1: Install Java

First, update your package list and install Java.

sudo apt update
sudo apt install openjdk-17-jre

# Jenkins Setup and Configuration Guide

## Access Jenkins

To log in to Jenkins, use the following URL:

http://<ec2-instance-public-ip>:8080


You can find the **public IP address** of your EC2 instance from your AWS EC2 console page.

## Note:
If you do not wish to allow **All Traffic** to your EC2 instance, follow these steps:

1. **Delete the inbound traffic rule** for your instance.
2. **Edit the inbound traffic rule** to only allow custom **TCP port 8080**.

## Jenkins Admin Login

After logging into Jenkins, you will be prompted for the administrator password. To get the **initial admin password**, run the following command on your EC2 instance:

sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Enter the Administrator password when prompted.

### Install Docker Pipeline Plugin
Follow the steps below to install the Docker Pipeline plugin in Jenkins:

Log in to Jenkins.
Go to Manage Jenkins > Manage Plugins.
In the Available tab, search for "Docker Pipeline".
Select the plugin and click the Install button.

After installation, restart Jenkins.
Docker Slave Configuration
To configure Docker on your Jenkins slave, follow these steps:

Update your package list and install Docker:


sudo apt update
sudo apt install docker.io
Grant the Jenkins user and Ubuntu user permission to access the Docker daemon:


sudo su -
usermod -aG docker jenkins
usermod -aG docker ubuntu
Restart Docker to apply the changes:

systemctl restart jenkins
systemctl restart docker

http://<ec2-instance-public-ip>:8080/restart
