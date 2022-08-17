# Install Apache Tomcat 10 and then Deploy a Java Web Application on Ubuntu 20.04
Apache Tomcat is a web server and servlet container that is used to serve Java applications. It’s an open source implementation of the Jakarta Servlet, Jakarta Server Pages, and other technologies of the Jakarta EE platform.
## Step 1 — Installing Tomcat
For security purposes, Tomcat should run under a separate, unprivileged user. Run the following command to create a user called tomcat:
```sh
sudo useradd -m -d /opt/tomcat -U -s /bin/false tomcat
```
<ins> *Note*</ins>  : By supplying /bin/false as the user’s default shell, you ensure that it’s not possible to log in as tomcat

You’ll now install the JDK. First, update the package manager cache by running:
```sh
sudo apt update
```
Then, install the JDK by running the following command:
```sh
sudo apt install default-jdk -y
```
Check the version of the available Java installation:
```sh 
java -version
```
The output should be similar to this:
> Output <br>
> openjdk version "11.0.14" 2022-01-18 <br>
> OpenJDK Runtime Environment (build 11.0.14+9-Ubuntu-0ubuntu2.20.04) <br>
> OpenJDK 64-Bit Server VM (build 11.0.14+9-Ubuntu-0ubuntu2.20.04, mixed mode, sharing) <br>
> 

To install Tomcat, you’ll need the latest Core Linux build for Tomcat 10, which you can get from the [downloads page](https://tomcat.apache.org/download-10.cgi). Select the latest Core Linux build, ending in .tar.gz. At the time of writing, the latest version was 10.0.20.

First, navigate to the `/tmp` directory:
```sh
cd /tmp
```
Download the archive using **wget** by running the following command:
```sh
wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.0.20/bin/apache-tomcat-10.0.20.tar.gz
```
The **wget** command downloads resources from the Internet.
Then, extract the archive you downloaded by running:
```sh
sudo tar xzvf apache-tomcat-10*tar.gz -C /opt/tomcat --strip-components=1
```
Since you have already created a user, you can now grant **tomcat** ownership over the extracted installation by running:
```sh
sudo chown -R tomcat:tomcat /opt/tomcat/
```
```sh
sudo chmod -R u+x /opt/tomcat/bin
```
Both commands update the settings of your tomcat installation. In this step, you installed the JDK and Tomcat. You also created a separate user for it and set up permissions over Tomcat binaries. You will now configure credentials for accessing your Tomcat instance.

## Step 2 — Configuring Admin Users
To gain access to the **Manager** and **Host Manager pages**, you’ll define privileged users in Tomcat’s configuration. You will need to remove the IP address restrictions, which disallows all external IP addresses from accessing those pages.

Tomcat users are defined in `/opt/tomcat/conf/tomcat-users.xml`. Open the file for editing with the following command:
