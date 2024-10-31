# maven阿里仓库镜像

```xml
<mirror>
    <id>aliyunmaven</id>
    <mirrorOf>central</mirrorOf>
    <name>aliyun maven</name>
   <url>https://maven.aliyun.com/repository/public</url>
    </mirror>
```

```xml
<!--  配置Maven中央仓库镜像地址  -->
<mirror>
<id>aliyunmaven</id>
<mirrorOf>*</mirrorOf>
<name>阿里云公共仓库</name>
<url>https://maven.aliyun.com/repository/public</url>
</mirror>
```

# springboot3运行测试方法报错解决(目前新版本似乎已修复)

在<mark>pom.xml</mark>里面加入以下内容

```xml
<properties>
    <mockito.version>4.5.1</mockito.version>
  </properties>
```

# proot-distro安装Ubuntu

### 安装Ubuntu

#### 安装proot-distro

```shell
pkg i proot-distro
```

#### 安装Ubuntu

```shell
proot-distro install ubuntu
```

### 启动Ubuntu

```shell
proot-distro login ubuntu --shared-tmp
```

### 安装基本环境

#### 更新源

```shell
apt update
```

#### 更新包

```shell
apt upgrade
```

#### 安装Java环境（nacos的依赖）

```shell
apt install openjdk-8-jdk
```

#### 安装erlang logrotate（rabbitmq的依赖）

```shell
apt install erlang logrotate
```

### 安装nacos（2.4.3）

#### 下载发行版

```shell
https://github.com/alibaba/nacos/releases
```

#### 解压

```shell
unzip nacos-*
```

#### 启动命令

```shell
bash startup.sh -m standalone
```

#### 访问地址

```shell
http://10.140.84.42:8848/nacos/
```

### 安装rabbitmq（3.12.3）

#### 下载3.12.3版本

```shell
https://objects.githubusercontent.com/github-production-release-asset-2e65be/924551/322c02df-8e6e-4b01-b951-659ed8f40380?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20241016%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241016T134454Z&X-Amz-Expires=300&X-Amz-Signature=a2dc0a25676a1c790e87b727c64f7b2169dd8311f42ee2ce72232566c3ab1acb&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Drabbitmq-server_3.12.3-1_all.deb&response-content-type=application%2Foctet-stream
```

#### 安装rabbitmq

```shell
dpkg -i rabbitmq-*
```

#### 启动rabbitmq

```shell
rabbitmq-server start &
```

#### 添加用户

```shell
rabbitmqctl add_user root root
```

#### 修改用户密码

```shell
rabbitmqctl change_password root 123456
```

#### 设置用户管理员标签

```shell
rabbitmqctl set_user_tags root administrator
```

#### 为用户设置权限

```shell
rabbitmqctl set_permissions -p / root '.*' '.*' '.*'
```

#### 开启插件rabbitmq_management以在浏览器中预览

```shell
rabbitmq-plugins enable rabbitmq_management
```

#### 访问地址

```shell
http://10.140.84.42:15672
```
