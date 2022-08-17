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

First, navigate to the /tmp directory:
