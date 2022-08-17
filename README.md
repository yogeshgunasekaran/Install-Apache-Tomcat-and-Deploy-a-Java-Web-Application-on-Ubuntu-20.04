# Install Apache Tomcat and Deploy a Java Web Application on Ubuntu 20.04
## 1. Install Java
Update system packages
 ```sh
 sudo apt update
 ```
 Install Java runtime environment
 ```sh
 sudo apt install default-jdk -y
 ```
 Verify Java installation
 ```sh
 java -version
 ```
 ## 2. Install Tomcat
Download the latest version of Apache Tomcat. To find the latest Tomcat version, visit the official download page
```sh
wget https://archive.apache.org/dist/tomcat/tomcat-10/v10.0.8/bin/apache-tomcat-10.0.8.tar.gz
```
Extract the downloaded archive
```sh
sudo tar xzvf apache-tomcat-10.0.8.tar.gz
```
Create an installation directory **/opt/tomcat/**
```sh
sudo mkdir /opt/tomcat/
```

Move the extracted files to the installation directory.
```sh
sudo mv apache-tomcat-10.0.8/* /opt/tomcat/
```
Change ownership of the installation directory.
```sh
sudo chown -R www-data:www-data /opt/tomcat/
```
Change access permissions for the installation directory.
```sh
sudo chmod -R 755 /opt/tomcat/
```
