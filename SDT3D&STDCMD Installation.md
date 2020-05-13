# SDT3D&STDCMD Installation

This document is installation manual for sdt3d & sdtcmd.

Recommend Environment
> OS - Ubuntu 18.04
> Default JDK - Oracle JDK 1.7.0__80
# Set Default Oracle JDK

Std3d is written by  Java using WorldWinds opensource JDK. 
Offical Std3d Document recommend to set Oracle JDK 1.7.0__80 as the system default JDK.
- Download Oracle JDK  - jdk-7u80-linux-x64.tar.gz
[https://www.oracle.com/java/technologies/javase/javase7-archive-downloads.html](https://www.oracle.com/java/technologies/javase/javase7-archive-downloads.html)
- Set Defualt JDK, Using update-alternatives
`sudo update-alternatives --install "/usr/bin/java" "java" "Directory where JAVA has been extracted>/bin/java" 1`
`sudo update-alternatives --install "/usr/bin/javac" "javac" "Directory where JAVA has been extracted>/bin/javac" 1`
`sudo update-alternatives --install "/usr/bin/jar" "jar" "Directory where JAVA has been extracted>/bin/jar" 1`
`sudo update-alternatives --install "/usr/bin/javadoc" "javadoc" "Directory where JAVA has been extracted>/bin/javadoc" 1`
- Set Environment variable - JAVA_HOME
`sudo nano /etc/profile`
-- add lines below
`JAVA_HOME=Directory where JAVA has been extracted>/jdk1.7.0__80`
`PATH=$PATH:$HOME/bin:$JAVA_HOME/bin`
`export JAVA_HOME`
`export PATH`
--reload environment using a command,
`. /etc/profile`

# Install Pre-Req package 
For building & install sdt,
There are some pre-req packages

## Install Linux package
` sudo apt-get install libxml2 libxml2-dev libvecmath-java libpcap-dev libnetfilter-queue-dev`

## Install ant.1.9.x

- Download - [apache-ant-1.9.14-bin.tar.gz](ftp://ftp.osuosl.org/pub/apache//ant/binaries/apache-ant-1.9.14-bin.tar.gz)
- Extract the .tar.gz file
- Set the ant for system
`sudo update-alternatives --install "/usr/bin/ant" "ant" "Directory where ant has been extracted>/bin/ant" 1`

## Install wxWidgets-2.8.12
- Install pre-req packages
` sudo apt-get install python-wxgtk2.8 python-wxtools wx2.8-i18n libwxgtk2.8-dev libgtk2.0-dev`
- Download - [wxWidgets-2.8.12.zip](https://github.com/wxWidgets/wxWidgets/releases/download/v2.8.12/wxMSW-2.8.12.zip)
- Extract the zip and Install
`cd wxWidgets-2.8.12`
`mkdir buildgtk`
`cd buildgtk`
`../configure --with-gtk \CFLAGS='-std=gnu++98' \CXXFLAGS='-std=gnu++98`
`make`
`sudo make install`
`ldconfig`

# Install SDT3D & SDTCMD

`git clone https://github.com/USNavalResearchLaboratory/sdt.git`
 `cd sdt/makefiles`
 `make -f Makefile_linux_amd64 all`

  After build&install  without any errors,
  You can get the sdt3d.zip ,Sdtcmd binary file and sdt bianry file.

 Sdt3d binary file is in the sdt3d.zip 