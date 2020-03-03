# Linux安装java和
## Ubuntu安装java
###### 解压缩并移动到指定目录
[java-linux-64位百度云下载](https://pan.baidu.com/s/1T6oNxpWvDzx67MGRhvaUGQ)&nbsp;&nbsp;&nbsp;提取码:d3fp

```
解压缩：tar -zxvf jdk-8u152-linux-x64.tar.gz
创建目录：mkdir -p /usr/local/java
移动安装包：mv jdk1.8.0_152/ /usr/local/java/
设置所有者：chown -R root:root /usr/local/java/
```

###### 配置环境变量

```
配置系统环境变量：vi /etc/environment
```

修改系统环境变量

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
export JAVA_HOME=/usr/local/java/jdk1.8.0_152
export JRE_HOME=/usr/local/java/jdk1.8.0_152/jre
export CLASSPATH=$CLASSPATH:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
```
配置用户环境变量：

```
vi /etc/profile
```

修改用户环境变量
```
if [ "$PS1" ]; then
  if [ "$BASH" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi
export JAVA_HOME=/usr/local/java/jdk1.8.0_152
export JRE_HOME=/usr/local/java/jdk1.8.0_152/jre
export CLASSPATH=$CLASSPATH:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH:$HOME/bin
if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi
```

使用户环境变量生效：

```
source /etc/profile
```

验证安装是否成功

```
java -version
# 输出如下
java version "1.8.0_152"
Java(TM) SE Runtime Environment (build 1.8.0_152-b16)
Java HotSpot(TM) 64-Bit Server VM (build 25.152-b16, mixed mode)
```
## 安装 Tomcat
解压缩并移动到指定目录

```
解压缩：tar -zxvf apache-tomcat-8.5.23.tar.gz
变更目录：mv apache-tomcat-8.5.23 tomcat
移动目录：mv tomcat/ /usr/local/
```

验证安装是否成功

```
启动：
/usr/local/tomcat/bin/startup.sh
./startup.sh
停止：
/usr/local/tomcat/bin/shutdown.sh
./shutdown.sh
```

