---
layout: post
title: Maven repository mirrors config in China
categories: Maven
description: Insert some config sentence in setting.xml
keywords: Maven
---

The central maven repository is so slow to download plugins and jars. Config maven seeting files to fasten the download speed.

config file /etc/maven/setting.xml

Memo: remeber to backup config file before you edit it.

$ sudo cp /etc/maven setting.xml /etc/maven/setting.xml.bk

This command will backup xml file in the same directory.

Now edit the file setting.xml

Insert mirror tags to mirrors tag.

```
<mirrors>
<mirror>    
      <id>repo2</id>    
      <mirrorOf>central</mirrorOf>    
      <name>Human Readable Name for this Mirror.</name>    
      <url>http://repo2.maven.org/maven2/</url>    
</mirror>    
<mirror>    
      <id>net-cn</id>    
      <mirrorOf>central</mirrorOf>    
      <name>Human Readable Name for this Mirror.</name>    
      <url>http://maven.net.cn/content/groups/public/</url>     
</mirror>    
<mirror>    
      <id>ui</id>    
      <mirrorOf>central</mirrorOf>    
      <name>Human Readable Name for this Mirror.</name>    
     <url>http://uk.maven.org/maven2/</url>    
</mirror>    
<mirror>    
      <id>ibiblio</id>    
      <mirrorOf>central</mirrorOf>    
      <name>Human Readable Name for this Mirror.</name>    
     <url>http://mirrors.ibiblio.org/pub/mirrors/maven2/</url>    
</mirror>    
<mirror>    
      <id>jboss-public-repository-group</id>    
      <mirrorOf>central</mirrorOf>    
      <name>JBoss Public Repository Group</name>    
     <url>http://repository.jboss.org/nexus/content/groups/public</url>    
</mirror>
</mirrors>
```
try it.  XIUXIUXIU~~~