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
<!-- 配置Maven中央仓库镜像地址 -->
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

# swagger在springboot3配置

1. 引入依赖

```xml

<dependencys>
    <dependency>
        <groupId>org.springdoc</groupId>
        <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
        <version>2.2.0</version>
    </dependency>
    <dependency>
        <groupId>io.swagger.core.v3</groupId>
        <artifactId>swagger-annotations</artifactId>
        <version>2.1.2</version>
    </dependency>
</dependencys>

```

2. 配置swagger

```java
/**
 * swagger配置文件
 */
@SpringBootConfiguration
@OpenAPIDefinition(info = @Info(
        title = "xxx系统", // api接口文档标题
        description = "xxx系统接口文档", // api接口文档描述
        version = "v2.0.0", // api接口版本
        termsOfService = "http://localhost:8080/", // api服务条款地址
        contact = @Contact(
                name = "作者姓名",
                email = "作者邮箱",
                url = "http://localhost:8080/"// 作者主页地址
        ),
        license = @License(
                name = "Apache 2.0", // 授权名称
                url = "https://www.apache.org/licenses/LICENSE-2.0.html"// 授权信息地址
        )
),
        servers = {
                @Server(
                        url = "http://localhost:8080/", // api服务地址
                        description = "本地服务器一服务"
                )
        },
        externalDocs = @ExternalDocumentation(
                description = "更多信息",
                url = "xxx"
        )
)
public class SwaggerConfig {

}
```

# mybatis逆向工程

1. 引入pom插件

```xml
<!--mybatis逆向工程插件-->
<plugin>
    <groupId>org.mybatis.generator</groupId>
    <artifactId>mybatis-generator-maven-plugin</artifactId>
    <version>1.4.2</version>
    <configuration>
        <overwrite>true</overwrite>
    </configuration>
    <dependencies>
        <dependency>
            <groupId>com.mysql</groupId>
            <artifactId>mysql-connector-j</artifactId>
            <scope>runtime</scope>
            <version>8.0.31</version>
        </dependency>
    </dependencies>
</plugin>
```

2. 配置generatorConfig.xml

将此文件放在resources目录下

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE generatorConfiguration
        PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
        "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">

<generatorConfiguration>
    <!--<classPathEntry location="/Program Files/IBM/SQLLIB/java/db2java.zip" />-->

    <context id="context" targetRuntime="MyBatis3">

        <!--suppressAllComments 设置为true 则不再生成注释-->
        <commentGenerator>
            <property name="suppressAllComments" value="true"/>
        </commentGenerator>
        <jdbcConnection driverClass="com.mysql.cj.jdbc.Driver"
                        connectionURL="jdbc:mysql://localhost:3306/security_study"
                        userId="root"
                        password="123456">
            <!--MySQL8必须加上这一句，不然生成会重复-->
            <property name="nullCatalogMeansCurrent" value="true"/>
        </jdbcConnection>

        <javaTypeResolver>
            <property name="forceBigDecimals" value="false"/>
        </javaTypeResolver>

        <!--生成实体-->
        <javaModelGenerator targetPackage="com.power.entity"
                            targetProject="E:\idea\project\power_security\security\src\main\java">
            <property name="enableSubPackages" value="true"/>
            <property name="trimStrings" value="true"/>
        </javaModelGenerator>

        <!--生成xml文件-->
        <sqlMapGenerator targetPackage="mapper"
                         targetProject="E:\idea\project\power_security\security\src\main\resources">
            <property name="enableSubPackages" value="true"/>
        </sqlMapGenerator>

        <!--生成dao接口-->
        <javaClientGenerator type="XMLMAPPER" targetPackage="com.power.dao"
                             targetProject="E:\idea\project\power_security\security\src\main\java">
            <property name="enableSubPackages" value="true"/>
        </javaClientGenerator>

        <!--生成所有表-->
        <table
                tableName="%">
            <!--enableDeleteByExample="false"-->
            <!--enableCountByExample="false"-->
            <!--enableUpdateByExample="false"-->
            <!--enableSelectByExample="false">-->
            <!--替换Sys字符串-->
            <domainObjectRenamingRule searchString="^Sys" replaceString=""/>
        </table>

    </context>
</generatorConfiguration>
```