# What's springboot?
## 1. springboot 帮我们快速、简单的创建一个独立的、生产级别的 spring 应用
+ 大多数 springboot 应用只需要编写少量配置即可快速整合 spring 平台和第三方技术
+ **特性：**
  + 快速创建独立 spring 应用 
    + SSM：导包、写配置、启动运行
  + 直接嵌入 Tomcat、Jetty or Undertow（无序部署 war 包）【 serverlet 容器】
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
### 1. 开发流程
1. pom.xml
> 所有springboot项目都必须继承自 spring-boot-starter-parent
```xml
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.2.2</version>
    </parent>
```
> 添加 web 开发的场景启动器
```xml
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>
```
> 编写代码
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
