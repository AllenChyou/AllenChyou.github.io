---
layout: post
title: JDK Environment Variables Config
categories: Java
description: Java config memo
keywords: Java
---

Java Develop Kit need to be find in system.

Edit /etc/profile, maybe need to be root.

Append these sentence.

export JAVA_HOME=/home/username/JavaDevEnv/jdk[version]
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

then logout and login.

Try some command

>java -version
