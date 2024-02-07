# spring boot 3.x 学习笔记
## 项目结构
1. 基本结构
   * src/main/java 程序开发以及主程序入口
   * src/main/resources 配置文件
   * src/test/java 测试程序
2. Spring Boot 建议的目录结果如下： 
   * root package 结构：com.example.myproject
     1. Application.java 建议放到根目录下面,主要用于做一些框架配置 
     2. model 目录主要用于实体与数据访问层（Repository） 
     3. service 层主要是业务类代码 
     4. controller 负责页面访问控制
## 项目初始化
1. 引入 web 模块
   1. pom.xml中添加支持web的模块：
   ```xml
   <dependency>
     <groupId>org.springframework.boot</groupId>
     <artifactId>spring-boot-starter-web</artifactId>
   </dependency>
   ```
   2. pom.xml 文件中默认有两个模块：
      * spring-boot-starter ：核心模块，包括自动配置支持、日志和 YAML，如果引入了 spring-boot-starter-web web 模块可以去掉此配置，因为 spring-boot-starter-web 自动依赖了 spring-boot-starter。
      * spring-boot-starter-test ：测试模块，包括 JUnit、Hamcrest、Mockito。


