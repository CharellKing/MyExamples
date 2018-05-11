# springboot知识点

## spring boot项目发布tomcat容器

### 设置spring boot项目

+ 修改打包方式

``` xml
<packaging>war</packaging>
```

+ 将spring boot中内嵌的tomcat包依赖排除

``` xml
<dependency>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-web</artifactId>
<exclusions>
<exclusion>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-tomcat</artifactId>
</exclusion>
</exclusions>
</dependency> 
```

** 注意: 如果要去掉，注释掉<exclusions>部分就可以了.**

+ 增加 SpringBootServletInitializer 子类，并覆盖它的 configure 方法

``` java
package com.quzhaojing;

import org.springframework.boot.builder.SpringApplicationBuilder;
import org.springframework.boot.web.servlet.support.SpringBootServletInitializer;

public class SpringBootStartApplication extends SpringBootServletInitializer {
@Override
protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
// 注意这里要指向原先用main方法执行的Application启动类
return builder.sources(Application.class);
}
}
```

+ 打包war包，发布到tomcat的webapp目录下，启动tomcat，自动解压war包，在浏览器中就可以访问了

```text
http://[tomcat部署IP]:[tomcat监听端口]/[war包名称]/[路由映射]
# http://192.168.0.47:38080/SpringDemo-1.0-SNAPSHOT/
```

# spring boot项目发布tomcat容器

## 设置spring boot项目

+ 修改打包方式

``` xml
<packaging>war</packaging>
```

+ 将spring boot中内嵌的tomcat包依赖排除

``` xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <exclusions>
        <exclusion>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
        </exclusion>
    </exclusions>
</dependency> 
```

** 注意: 如果要去掉，注释掉<exclusions>部分就可以了.**

+ 增加 SpringBootServletInitializer 子类，并覆盖它的 configure 方法

``` java
package com.quzhaojing;

import org.springframework.boot.builder.SpringApplicationBuilder;
import org.springframework.boot.web.servlet.support.SpringBootServletInitializer;

public class SpringBootStartApplication extends SpringBootServletInitializer {
    @Override
    protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
        // 注意这里要指向原先用main方法执行的Application启动类
        return builder.sources(Application.class);
    }
}
```

+ 打包war包，发布到tomcat的webapp目录下，启动tomcat，自动解压war包，在浏览器中就可以访问了

```text
http://[tomcat部署IP]:[tomcat监听端口]/[war包名称]/[路由映射]
# http://192.168.0.47:38080/SpringDemo-1.0-SNAPSHOT/
```

**注意: tomcat的支持的servlet版本必须与依赖的spring boot的版本一致**



## 参考

引用:

[spring boot项目发布tomcat容器（包含发布到tomcat6的方法） - weixliu - 博客园](https://www.cnblogs.com/weixliu/p/6432342.html)








### 参考

引用:

[spring boot项目发布tomcat容器（包含发布到tomcat6的方法） - weixliu - 博客园](https://www.cnblogs.com/weixliu/p/6432342.html)



