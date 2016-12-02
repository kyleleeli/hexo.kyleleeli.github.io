---
title: Java生态系统
date: 2016-12-02 12:24:07
tags:
- Java 
- microservice 
- bigdata
permalink: java-ecosystem
---

# Java生态系统

### 成长过程（历史）
 + 作者：James Gosling（詹姆斯·高斯林）

 ![James Gosling](https://upload.wikimedia.org/wikipedia/commons/thumb/1/14/James_Gosling_2008.jpg/239px-James_Gosling_2008.jpg)

 + 1995.5 Sun公司推出Java语言，2010被Oracle收购
  > 名称由来：最早叫Oak（橡树），但因为被别的公司注册，所以决定再重新起名，排名第一的 **Silk（丝绸）** 遭到Gosling反对，第二、第三（Lyric（抒情诗））没有通过商标律师，排名第四的 **Java** 最终通过，Java是印度尼西亚爪哇岛的英文名称，因盛产咖啡而闻名，国外的许多咖啡店用Java来命名或宣传，以彰显其咖啡的品质。Java语言中的许多库类名称，多与咖啡有关，如JavaBeans（咖啡豆）、NetBeans（网络豆）以及ObjectBeans （对象豆）等等。
 
 + 语言特性：OO、跨平台、泛型编程
 + 号称“Write Once, Run Anywhere”
 + 版本：
   - JDK 1.0 (January 21, 1996)
   - JDK 1.1 (February 19, 1997)
   
   > 技术：JAR文件格式、JDBC、JavaBeans、RMI。  
   语法：内部类（Inner Class）和反射（Reflection）。

   - J2SE 1.2 (December 8, 1998)
   - J2SE 1.3 (May 8, 2000)
   - J2SE 1.4 (February 6, 2002) 
   - J2SE 5.0 (September 30, 2004)
   > 重大更新，泛型支持、基本类型的自动装箱、改进的循环、枚举类型、格式化I/O及可变参数
   - Java SE 6 (December 11, 2006)
   - Java SE 7 (July 28, 2011)
   - Java SE 8 (March 18, 2014)

   ![java release dates](assets/java/java-release-dates.png)

   ![java features](assets/java/java-features2.png)
    
   > **SE** : Standard Edition，包含Java语言核心的类。比如：数据库连接、接口定义、输入/输出、网络编程。  
   **EE** : Enterprise Edition，包含JSE中的类，并且还包含用于开发企业级应用的类。 比如：EJB、servlet、JSP、XML、事务控制。  
   **ME** : Micro Edition，包含嵌入式开发或者移动应用开发所需要的类，包括一些JSE的核心代码和一些无线设备的API。  

   ![](assets/java/java-ee-7-update.jpg)

   ---
   > **JDK** : Java Development Kit，软件开发工具包，包含JRE和java工具（编译器javac、打包jar、文档生成器javadoc、调试jdb、运行java）  
   **JRE** : Java Runtime Environment，java运行时环境，包含JVM和java核心库及支持文件    
   **JVM** : Java Virtual Machine，java虚拟机，Java虚拟机有自己完善的硬体架构，如处理器、堆栈、寄存器等，还具有相应的指令系统。
   JVM屏蔽了与具体操作系统平台相关的信息，使得Java程序只需生成在Java虚拟机上运行的目标代码（字节码），就可以在多种平台上不加修改地运行。  
   所以，除了java外，也可以运行其他语言，比较流行的如：Scala、Groovy

   ![jdk-jre-JVM](assets/java/jdk-jre-jvm-diff.png)

   ![jdk jre jvm difference](assets/java/jdk-jre-jvm-diff2.png)

   ---
   > **JDK** : 默认指的是Sun公司发布的jdk，但也有很多公司和组织自己研发专属的jdk  
   **Open JDK** : JDK的开放原始码版本  
   
   ![jdk-openjdk](assets/java/jdk-openjdk-relation.jpg)

   区别：

   |    | JDK | Open JDK|
   |--- |---|---|
   |协议 | JRL(JavaResearch License，Java研究授权协议)| GPL(General Public License) V2|
   |代码完整度| 完整 | 从JDK7开始差距不大，缺少 SNMP |
   |工具 | 完整 | 缺少部分工具，并且尽量分离|

   > **JCP** : Java Community Process，开放性国际组织
   **JSR** : Java Specification Requests，新功能或特性需提交JCP整理并规范为JSR，然后经过JCP执行委员会投票决定。

### 繁衍子嗣（社区及衍生品）
 
  + Web：Spring MVC、Spring Boot、JSF、Structs
  + RPC：Dubbo、Dubbox、Thrift
  + ORM：Hibernate、MyBatis
  + J2EE：Spring
  + 移动：Android
  + JSON：fastjson
  + 全文搜索：Lucene
  + ETL工具：Kettle
  + 模板引擎：Velocity、thymeleaf
  + 构建：Maven、Gradle、Ant
  + 应用服务器：Tomcat(Apache基金会)、Jetty、Wildfly、JBoss(Redhat)、WebLogic(Oracle)、WebSphere(IBM)
  + 持续集成：Jenkins
  + 分布式存储：Cassandra
  + 消息服务：ActiveMQ、RabbitMQ
  + 作业调度：Quartz
  + 单点登录：OpenSSO
  + 分布式搜索：ElasticSearch
  + 日志管理：Logstash
  + 动态脚本语言：Groovy
  + 单元测试：JUnit

#### 应用开发

  + Spring vs Java EE

  ![spring vs java ee](assets/java/javaee-vs-spring.jpg)

#### 微服务
  + Spring Boot VS Java EE

  ![spring boot vs java ee](assets/java/microservices-java-ee-vs-spring-boot.jpg)

  ![spring cloud vs java ee](assets/java/microservices-java-ee-vs-spring-cloud.jpg)

#### 大数据

  ![Hadoop Ecosystem](assets/java/hadoop-ecosystem.jpg)

  [开源项目](https://java-source.net/)


### 大众脸？还是美人胚子？（流行度）

#### 语言

- Redmonk

![redmonk languages rank](assets/java/redmonk-lang-rank-2016Q3.png)

- Tiobe

![tiobe languages rank](assets/java/tiobe-lang-rank-201611.png)

![tiobe languages rank](assets/java/tiobe-lang-rank-201611-2.png)

#### Java工具和技术调查

[原文链接](http://zeroturnaround.com/rebellabs/java-tools-and-technologies-landscape-2016/)

- 总览：
> 68% 的开发者用 Maven；  
68% 的在用 Git；  
46% 的在用 Intellij IDEA;  
43% 的在用 Spring MVC  
34% 的在用 微服务架构；  
32% 的在用 Docker；  

![总览](assets/java/java_report/summary-1.png)

> 62% 的在用 Java 8；  
60% 的在用 Jenkins;  
42% 的在用 Tomcat;  
39% 的在用 Oracle DB;  
31% 的在用 Java EE 7;  
29% 的在用 Spring Boot;  

![总览](assets/java/java_report/summary-2.png)

- 工作年限
> 大部分在5-20之间

![v](assets/java/java_report/years-of-experience.png)

- 项目类型
> 67%是全栈

![项目类型](assets/java/java_report/application-type-breakdown.png)

- 微服务
![微服务](assets/java/java_report/microservices-plans-and-results.png)

- JVM语言

![JVM语言](assets/java/java_report/jvm-languages-v1.jpg)

- Java版本

![Java版本](assets/java/java_report/java-version-breakdown.png)

- Java EE版本

![Java EE版本](assets/java/java_report/java-ee-breakdown.png)

- IDE

![IDE](assets/java/java_report/ide.png)

- 构建工具

![构建工具](assets/java/java_report/build-tools.png)

- 应用服务器
> 蓝色：生产环境，黄色：开发环境

![应用服务器](assets/java/java_report/app-servers.png)

- 数据库

![数据库](assets/java/java_report/databases.png)

- 总结
> 2040 名开发者参与调查；  
  做全栈Web项目的开发者，平均大约有 10 - 12 年的工作经验；  
  63% 的在大企业或中型工作就职；  
  74% 的自认为高于业界平均水平；  
  34% 采用了微服务架构；  
  66% 并没有采用微服务，其中仅有 12% 的在未来有计划试试；  
  Java 8 是主流，62% 的参与者已经在生产环境用上了；  
  Java EE 7 ， 31% 的参与者已经在用新版本了；  
  42% 的根本不用 Java EE；  
  46% 的在用 IntelliJ IDEA，已超过了 Eclipse 的 41%；  
  68% 的在用 Maven ，Gradle 只有 16%.  
  Tomcat 是最受欢迎的应用服务器，高达 42%；  
  39% 的参与者在用 Oracle DB  ，稍微比 MySQL 的 38% 高了一点；  
  MongoDB 在最受欢迎的 NoSQL DB ，比例是 15% ；  
  Spring 依旧主宰着 Web 框架市场， Spring MVC 和 Spring Boot 的比例是 43% 和 29%；  
  Jenkins 主宰着 CI Server 市场，比例是 60% ；  
  Git 有 68% 份额，而 SVN 仅有 23%；  
  New Relic 在 APMs 有着 11% 份额；  
  32% 的参与者在用 Docker ，但 54% 的根本没用虚拟化环境；  
  71% 的参与者宣称自己是 Agile 的；  

- 过去4年变化
> Eclipse 的份额持续下降，而 IntelliJ 却稳步持续上升，已经在使用率超越了 Eclipse；  
  Maven 依旧保持着绝对的领先优势；  
  Gradle 增长缓慢，暂时还不足以挑战 Maven；  
  Spring 主宰着 Web 框架市场，从 2012 年到 2016 年持续增长中，特别是 Spring Boot 可以称为剧增；  
  JSF 在缓慢下降。Stripes、Tapestry、Wicket 和 Play 1 看样子要退出历史舞台了；  
  Git 展示了强劲的增长，从 27% 到 68%。而 SVN 却从 55% 降到 23%；  

- 常用开发工具

  ![popular java frameworks and tools](assets/java/most-popular-java-frameworks-and-tools-2016.png)


#### 就业

> 全文涉及的城市包括： 北京、上海、深圳、广州、杭州、成都、南京、武汉、西安、长沙、苏州 。  
涉及的语言包括：Java、Python、PHP、C#、C++  
数据来源：使用Python爬取的拉勾网的招聘信息（共计15059条招聘信息）

![](assets/java/offer-report/lang-rank.png)
> 主流：Java、PHP、C++

![](assets/java/offer-report/lang-payment.png)
> 数据：按照拉勾网上薪资区间最低的价格来进行统计展示  
Python语言以11.9k的薪资领跑，最低的是C#的8.6k

![](assets/java/offer-report/lang-xueli.png)
> C++的招聘看重学历，大部分企业需要开发者有硕士及以上学历  
PHP的招聘基本上不注重学历  
对Java开发者的要求是本科学历即可   

![](assets/java/offer-report/lang-city.png)
> 各城市的Java需求都很大  
北上深三城市对C++的需求是相对较多的，这三个城市是C++开发者的最佳选择  
北京对Python开发者需求也较大，其它城市需求量不是特大  
C#在所有城市普遍需求不大  
北上广深杭对PHP的需求极大仅次于Java的需求  

![](assets/java/offer-report/lang-city-payment.png)
> 成都、南京、武汉、西安、长沙只要你是个程序员不管你用什么语言做开发，平均工资都是那么点6-9k，南京完完全全的几乎重叠。  
因此，想安稳拿高薪啊：学Java去北上深杭吧！  
长沙这个城市为什么C#开发者平均薪资最高啊？！对了，Python开发者千万别去长沙，最低平均薪资。  

### 大公司使用情况
  + 阿里 占90%
  + 百度、腾讯，主流：C、C++
  + 华为
  + Twitter 2012年开始从Ruby on Rails转向到Java+Scala
  + Amazon、Google、eBay

### A-Z
  + A : **AspectJ**（AOP框架）
  + B : **Spring Boot**
  + C : **Clojure**（运行在JVM上的动态语言）
  + D : **Dagger**（Android平台的依赖注入框架）
  + E : **Ektorp**（Ektorp is a Java persistence API that uses CouchDB as storage engine）
  + F : **Felix**（Apache Felix is a community effort to implement the OSGi Framework and Service platform and other interesting OSGi-related technologies under the Apache license）
  + G : **Groovy & Grails**（Groovy是Java平台上设计的面向对象编程语言。 这门动态语言拥有类似Python、Ruby和Smalltalk中的一些特性，可以作为Java平台的脚本语言使用。Grails : Web application framework, Groovy version of Ruby on Rails, to use in Java development. ）
  + H : **Spring HATEOAS**（Create REST representations that follow the HATEOAS principle from your Spring-based applications.）
  + I : **Ivy**（Apache Ivy™ is a popular dependency manager focusing on flexibility and simplicity.）
  + J : **Jetty**（Jetty provides a Web server and javax.servlet container, plus support for HTTP/2, WebSocket, OSGi, JMX, JNDI, JAAS and many other integrations.）
  + K : **Kotlin**（）
  + L : **Lucene**（Apache Lucene and Solr are distributed under a commercially friendly Apache Software license）
  + M : **Morphia**（The Java Object Document Mapper for MongoDB）
  + N : **Nashorn**（Nashorn is a JavaScript engine developed in the Java programming language by Oracle.）
  + O : **OpenXava**（OpenXava is an AJAX Java Framework for Rapid Development of Enterprise Web Applications.）
  + P : **Play**（The High Velocity Web Framework for Java and Scala）
  + Q : **QPid**（Apache Qpid makes messaging tools that speak AMQP and support many languages and platforms. ）
  + R : **Rave**（Apache Rave moved into the Attic in January 2016. Apache Rave was a web and social mashup engine that aggregated and served web widgets. It was targeted as an engine for internet and intranet portals.）
  + S : **Stripes**（Stripe provides a set of unified APIs and tools that instantly enable businesses to accept and manage online payments.）
  + T : **Thymeleaf**（Thymeleaf is a modern server-side Java template engine for both web and standalone environments. ）
  + U : **UIMA**
  + V : **VertX**
  + W : **Wookie**
  + X : **Xindice**
  + Y : **YamlBeans**
  + Z : **Zookeeper**（Apache ZooKeeper is an effort to develop and maintain an open-source server which enables highly reliable distributed coordination.）

### 参考
  + [维基百科](https://zh.wikipedia.org/wiki/Java)
  + [2016 年 Java 工具和技术的调查：IDEA 已超过 Eclipse](https://mp.weixin.qq.com/s?__biz=MjM5NzMyMjAwMA==&mid=2651477527&idx=1&sn=bab8771112cd9e8ed3ce0e2170d5a469&chksm=bd253a688a52b37efc14771d272008110b5e0375756f8f1178c19c7527025cce90eb52f2e449&scene=0&key=9289b6ec21f92a591bd7da4131f55d9ea14aa18499bfabb9f98a2521f682f6149656b9d2c6c71d96b16b11d5b86d07d3&ascene=7&uin=MjAyNjIyNTc0MQ%3D%3D&devicetype=android-23&version=26031933&nettype=WIFI&pass_ticket=dcoW4KAwlRHuuNy3CJAOPDyuYKwNMIotaQwWxXSsO3e9G1B5M5xEWSWQFrKSEARi&wx_header=1)
  + [Java/Python/PHP/C#/C++各大城市招聘状况分析](https://zhuanlan.zhihu.com/p/23661167)
  + [语言流行度调查-redmonk](http://redmonk.com/sogrady/category/programming-languages/)
  + [语言流行度调查-tiobe](http://www.tiobe.com/tiobe-index/)
  + [极客学院｜《2016年中国程序员职业薪酬报告 》完整版发布](http://mp.weixin.qq.com/s?__biz=MjM5ODE0MTM1MA==&mid=2650227512&idx=1&sn=073920372d8cbd032b070218dc3e195e&scene=4)
  + [The Hadoop Ecosystem Table](https://hadoopecosystemtable.github.io/)
  + [Java Tools and Technologies Landscape Report 2016](http://zeroturnaround.com/rebellabs/java-tools-and-technologies-landscape-2016/)
  + [Awesome Microservices](https://github.com/mfornos/awesome-microservices)