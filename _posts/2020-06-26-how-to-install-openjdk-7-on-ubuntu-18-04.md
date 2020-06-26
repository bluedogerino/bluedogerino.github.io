---
layout: post
title:  "How to install OpenJDK 7 on Ubuntu 18.04"
categories: tutorial cloud ubuntu openjdk 7 18.04 lineage
img: GA1pr7V.png
---

Hello there,
if you're viewing this page you have probably tried building an older version of lineage (i.e. cm-13 and such)
and you arrived at an error that looks something like this 
```Error: could not find jdk tools.jar, please check if your JDK was installed correctly.```
Now this error probably occured because you are using a openjdk that's newer than OpenJDK version specific for your LineageOS version.
As we can see in the official build guide from LineageOS Wiki, OpenJDK 1.7 is needed to build
![lineagewiki-java](https://i.imgur.com/keEdYY3.png)

Ok, so to install OpenJDK 7 , it's a bit of a tricky process, but I hope my guide will assist you in achieving that.
Let's get started!

1.Open up a terminal (for most distros it's Ctrl+Alt+T, but if your's doesn't open one up, look up terminal in your application list)
------
For purposes of this tutorial I will be using a WSL 2 machine, but this applies to all variants of Ubuntu/Debian derivatives.
![terminal](https://i.imgur.com/qEpwzmw.png)
 
2.Do ```cd ~/Downloads``` and then ```wget https://gitlab.com/bosniandoge/openjdk-7-repos/-/raw/master/jdk-7u80-linux-x64.tar.gz```
------
![terminal2](https://i.imgur.com/oAikog3.png)

3.Next step is to create a directory in the location ```/usr/local/java``` and copy the file we just downloaded there 
------
![terminal3](https://i.imgur.com/gNaUYzL.png)

4.What we need to do after copying the file is to enter the directory we previously created and extract the tarball we copied to it
------
![terminal4](https://i.imgur.com/jZAY44b.png)

To check if the files extracted correctly do ```ls -a```
![terminal5](https://i.imgur.com/k7zxcsh.png)

5.Open /etc/profile in nano with sudo privileges and copy the following text at the bottom of the file (PageDown for quicker navigation to the bottom of the file):
------
```
JAVA_HOME=/usr/local/java/jdk1.7.0_80
JRE_HOME=/usr/local/java/jdk1.7.0_80 
PATH=$PATH:$JRE_HOME/bin:$JAVA_HOME/bin

export JAVA_HOME
export JRE_HOME
export PATH
```
![terminal6](https://i.imgur.com/rIQEhWJ.png)

6.After saving the file, the next thing you should do is do the following commands, they will update all the paths to the openjdk-7:
------
```
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jdk1.7.0_80/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.7.0_80/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jdk1.7.0_80/bin/javaws" 1
sudo update-alternatives --set java /usr/local/java/jdk1.7.0_80/bin/java
sudo update-alternatives --set javac /usr/local/java/jdk1.7.0_80/bin/javac
sudo update-alternatives --set javaws /usr/local/java/jdk1.7.0_80/bin/javaws
```

![java-alternatives](https://i.imgur.com/QzLSelk.png)
After u do the following commands, you should reload the profile by using ```source /etc/profile```
![reload-profile](https://i.imgur.com/xXPTEeh.png)

7.Check your Java version by doing ```java -version
------
![final](https://i.imgur.com/grb7zUd.png)
If it shows u the same output as the picture above you have successfully installed OpenJDK 7.

That's it, thank you for reading. :D


