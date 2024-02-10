# What's springboot?
## 1. springboot 帮我们快速、简单的创建一个独立的、生产级别的 spring 应用
+ 大多数 springboot 应用只需要编写少量配置即可快速整合 spring 平台和第三方技术
+ **特性：**
  + 快速创建独立 spring 应用 
    + SSM：导包、写配置、启动运行
  + 直接嵌入 Tomcat、Jetty or Undertow（无需部署 war 包）【 serverlet 容器 】
    +  linux tomcat mysql：war 放到 tomcat 的 webapps 下
    +  jar：部署环境有 java 环境即可 java -jar
  + 提供可选的 starter，简化应用整合
    + **场景启动器（ starter ）**：web、json、邮件、oss（存储对象）、异步、定时任务、缓存...
    + 导包一堆，控制好版本
    + 为每一种场景准备了一个依赖：web-starter、mybatis-starter
  + 按需自动配置 Spring 以及第三方库 
    + 如果这些场景我要使用(生效)，这个场景的所有配置都会自动配置好
    + 约定大于配置：每个场景都有很多默认配置
    + 自定义：配置文件中修改几项就可以
  + 提供生产级特性： 如监控指标、健康检查、外部化配置等
    + 监控指标、健康检查（k8s）、外部化配置
  + 无代码生成、无 xml
## 2. 快速体验
> 场景：浏览器发送 /hello 请求，返回“hello，spring boot3
### 开发流程
1. 创建一个 maven 项目，导入场景
> 所有springboot项目都必须继承自 spring-boot-starter-parent
```xml
    <!-- pom.xml -->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.2.2</version>
    </parent>
```
> 添加 web 开发的场景启动器
```xml
    <!-- pom.xml -->    
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>
```
2. 实现一个基本项目（基于官方文档说明）
> 主程序
```java
/**
 * MainApplicaiton.java
 */
@SpringBootApplication
public class MainApplicaiton {
    public static void main(String[] args) {
        SpringApplication.run(MainApplicaiton.class, args);
    }
}
```
> 业务代码
```java
/**
 * controller/HelloController.java
 */
@RestController
public class HelloController {
  @GetMapping("/hello")
  public String Hello(){
    return "Hello, Spring boot3!";
  }
}

```
> 创建可执行 jar 包, 首先添加 Springboot 应用打包插件, 然后执行 mvn clean package
```xml
    <!-- pom.xml -->
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
```
> 使用命令执行打包后的文件
```dos
java -jar demo.jar
```
## 特性小结
### 1. 简化整合
导入相关的场景，拥有相关的功能 => 场景启动器
> 默认支持的所有场景：https://docs.spring.io/spring-boot/current/reference/html/using.html#using.build-systems.starters
+ 官方提供的场景，命名为：spring-boot-starter-*
+ 第三方提供场景，命名为：*-sprint-boot-starter
场景一导入，万物皆就绪
### 2. 简化开发
无需编写任何配置，直接开发业务
### 3. 简化配置
> application.properties
```properties
server.port = 8888
server.address = 0.0.0.0
```

