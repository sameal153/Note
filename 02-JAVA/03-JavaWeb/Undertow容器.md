# 简介
## 概述
Undertow 是红帽公司开发的一款基于 NIO 的高性能 Web 嵌入式服务器。

Undertow 是一个采用 Java 开发的灵活的高性能 Web 服务器，提供包括阻塞和基于 NIO 的非堵塞机制。Undertow 是红帽公司的开源产品，是 Wildfly 默认的 Web 服务器。

Undertow 提供一个基础的架构用来构建 Web 服务器，这是一个完全为嵌入式设计的项目，提供易用的构建器 API，完全兼容 Java EE Servlet 3.1 和低级非堵塞的处理器。

## 特点
轻量级：它是一个 Web 服务器，但不像传统的 Web 服务器有容器概念，它由两个核心 Jar 包组成，加载一个 Web 应用可以小于 10MB 内存
- **HTTP/2 Support** Undertow 支持 HTTP/2 开箱即用，不需要重写引导类路径。
- **支持 HTTP 升级** 支持 HTTP 升级，允许多个协议通过 HTTP 端口上进行复用。
- **支持 Web Socket** Undertow 提供对 Web 套接字的全面支持，包括对 JSR-356 的支持。
- **支持 Servlet 4.0** Undertow 提供了对 Servlet 4.0 的支持，包括对嵌入式 Servlet 的支持，还可以混合部署 Servlet 和原生 Undertow 非阻塞处理程序。
- **可嵌入式** Undertow 可以嵌入到应用程序中，也可以通过几行代码独立运行。
- **高灵活性** 一个 Undertow 服务器是通过链式处理器来配置的，可以根据需要添加功能，因此可以避免添加没有必要的功能。
## 性能对比
大概的结论是：综合吞吐量，响应时间以及资源消耗，Undertow胜出

1. 吞吐量及响应时间
    1. 吞吐量：Undertow > Jetty > Tomcat
    2. 响应时间：Jetty < Tomcat < Undertow
2. CPU使用率：Undertow < Jetty < Tomcat
3. 内存使用率：Undertow < Jetty < Tomcat
4. 线程数：Undertow < Jetty < Tomca

## 替换tomcat为Undertow容器

> 这里以一个Helloworld项目（）为例，在此基础上移除内[SpringBoot入门 - 创建第一个Hello world工程](https://pdai.tech/md/spring/springboot/springboot-x-hello-world.html)嵌的Tomcat并使用Undertow。

### [#](#移除内嵌的tomcat并使用undertow)移除内嵌的Tomcat并使用Undertow

移除内嵌的Tomcat相关的依赖spring-boot-starter-tomcat，并增加undertow的依赖spring-boot-starter-undertow

```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <exclusions>
        <exclusion>
            <artifactId>spring-boot-starter-tomcat</artifactId>
            <groupId>org.springframework.boot</groupId>
        </exclusion>
    </exclusions>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-undertow</artifactId>
</dependency>
```

### [#](#配置undertow) 配置Undertow

Undertow相关的配置可以看：
![Pasted image 20240130184705](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404091001318.png)

### [#](#简单测试) 简单测试

运行SpringBootApplication

结果如下

![Pasted image 20240130184715](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404091002682.png)运行的日志如下

```

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v2.5.3)

2022-04-18  22:47:28.900  INFO 60368 --- [           main] .p.s.h.u.SpringBootHelloWorldApplication : Starting SpringBootHelloWorldApplication using Java 1.8.0_181 on MacBook-Pro.local with PID 60368 (/Users/pdai/pdai/www/tech-pdai-spring-demos/105-springboot-demo-helloworld-undertow/target/classes started by pdai in /Users/pdai/pdai/www/tech-pdai-spring-demos)
2022-04-18  22:47:28.902  INFO 60368 --- [           main] .p.s.h.u.SpringBootHelloWorldApplication : No active profile set, falling back to default profiles: default
2022-04-18  22:47:29.691  WARN 60368 --- [           main] io.undertow.websockets.jsr               : UT026010: Buffer pool was not set on WebSocketDeploymentInfo, the default pool will be used
2022-04-18  22:47:29.710  INFO 60368 --- [           main] io.undertow.servlet                      : Initializing Spring embedded WebApplicationContext
2022-04-18  22:47:29.710  INFO 60368 --- [           main] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 769 ms
2022-04-18  22:47:30.020  INFO 60368 --- [           main] io.undertow                              : starting server: Undertow - 2.2.9.Final
2022-04-18  22:47:30.025  INFO 60368 --- [           main] org.xnio                                 : XNIO version 3.8.4.Final
2022-04-18  22:47:30.029  INFO 60368 --- [           main] org.xnio.nio                             : XNIO NIO Implementation Version 3.8.4.Final
2022-04-18  22:47:30.060  INFO 60368 --- [           main] org.jboss.threads                        : JBoss Threads version 3.1.0.Final
2022-04-18  22:47:30.121  INFO 60368 --- [           main] o.s.b.w.e.undertow.UndertowWebServer     : Undertow started on port(s) 8080 (http)
2022-04-18  22:47:30.132  INFO 60368 --- [           main] .p.s.h.u.SpringBootHelloWorldApplication : Started SpringBootHelloWorldApplication in 1.586 seconds (JVM running for 2.215)
```



