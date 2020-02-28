# 个人常用Dockerfile
## 3.6.1-jdk-8-alpine-aliyun
### Dockerfile
```dockerfile
FROM maven:3.6.1-jdk-8-alpine

COPY settings.xml /usr/share/maven/ref/
```
### settings.xml
```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      https://maven.apache.org/xsd/settings-1.0.0.xsd">
  <localRepository>/usr/share/maven/ref/repository</localRepository>
  <mirrors>
    <mirror>
        <!--This sends everything else to /public -->
        <id>aliyun-nexus</id>
        <mirrorOf>*</mirrorOf>
        <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
    </mirror>
    <mirror>
        <!--This is used to direct the public snapshots repo in the 
            profile below over to a different nexus group -->
        <id>aliyun-nexus-public-snapshots</id>
        <mirrorOf>public-snapshots</mirrorOf>
        <url>http://maven.aliyun.com/nexus/content/repositories/snapshots/</url>
      </mirror>
    </mirrors>
</settings>
```
