
---

---

# Spring Session

Rob Winch, Vedran Pavić, Jakub Kubrynski

Version 1.3.1.RELEASE

---

### Spring Session提供了一个用于管理用户会话信息的API和实现。

# 1.简介

Spring Session提供了一个用于管理用户会话信息的API和实现。 它还提供了与HttpSession和WebSocket透明的集成：

nHttpSession -允许在应用程序容器（即Tomcat）中替换HttpSession。 其他功能包括：

l集群Session支持 - Spring Session使得集群Session非常简单，这使得集群Session的解决方案不依赖于应用程序容器特定的解决方案。

l多个浏览器会话支持 - Spring Session支持在单个浏览器实例中管理多个用户的会话（即与Google类似的多个经过身份验证的帐户）。

lRESTful API支持 - Spring Session允许在Http请求头中提供会话ID以使用RESTful API

nWebSocket -提供了在接收WebSocket消息时保持HttpSession处于激活状态的功能。

# 2.Spring Session1.3的新特性

以下是Spring Session 1.3中主要的新功能。 如果需要了解完整的更新情况，请参考1.3.0.M1，1.3.0.M2，1.3.0.RC1和1.3.0.RELEASE的更新日志。

* 支持Hazelcast
* 支持Spring Security的并发会话管理
* 添加了OrientDB社区扩展。
* GenericJackson2JsonRedisSerializer参考示例和Spring Security的新Jackson支持
* Lettuce参考指南
* spring.session.cleanup.cron.expression可用于覆盖清理任务的cron表达式。
* 许多性能上的改进和bug修复

# 3.示例与入门指南

如果您初次使用Spring Session，那么最好参考我们提供的示例程序。

| 来源 | 描述 | 参考 |
| :--- | :--- | :--- |
| [HttpSession](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/httpsession) | 演示Spring Session来替换HttpSession，使用Redis作为Session存储容器。 | [HttpSession Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/httpsession.html) |
| [HttpSession XML](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/httpsession-xml) | 演示Spring Session基于XML的配置方式来替HttpSession， 使用Redis作为Session存储容器。 | [HttpSession XML Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/httpsession-xml.html) |
| [HttpSession with GemFire using Spring Boot](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/httpsession-gemfire-boot) | 演示Spring Session在Spring Boot应用程序中使用Client / Server拓扑替换HttpSession，使用GemFire作为Session 存储容器。 |  |
| [HttpSession with GemFire \(Client/Server\)](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/httpsession-gemfire-clientserver) | 演示Spring Session使用Client / Server拓扑替HttpSession，使用GemFire作为Session 存储容器。 | [HttpSession GemFire Client/Server Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/httpsession-gemfire-clientserver.html) |
| [HttpSession with GemFire \(Client/Server\) using XML](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/httpsession-gemfire-clientserver-xml) | 演示Spring Session基于XML的配置方式，使用Client / Server拓扑替HttpSession，将GemFire作为Session 存储容器。 | [HttpSession GemFire Client/Server XML Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/httpsession-gemfire-clientserver-xml.html) |
| [HttpSession with GemFire \(P2P\)](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/httpsession-gemfire-p2p) | 演示Spring Session使用P2P拓扑替HttpSession，将GemFire作为Session 存储容器。 | [HttpSession GemFire P2P Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/httpsession-gemfire-p2p.html) |
| [HttpSession with GemFire \(P2P\) using XML](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/httpsession-gemfire-p2p-xml) | 演示Spring Session基于XML的配置方式，使用P2P拓扑替换HttpSession，将GemFire作为Session 存储容器。 | [HttpSession GemFire P2P XML Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/httpsession-gemfire-p2p-xml.html) |
| 自定义[Cookie](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/custom-cookie) | 演示Spring Session如何使用自定义Cookie | [Custom Cookie Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/custom-cookie.html) |
| [Spring Boot](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/boot) | 演示如何在Spring boot应用中使用Spring Session。 | [Spring Boot Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/boot.html) |
| [Grails 3](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/grails3) | 演示在Grails3中使用Spring session | [Grails 3 Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/grails3.html) |
| [Spring Security](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/security) | 演示如何在Spring Security应用中使用Spring session | [Spring Security Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/security.html) |
| [REST](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/rest) | 演示如何在REST应用程序中使用Spring Session来支持使用Http请求头进行身份验证。 | [REST Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/rest.html) |
| [Find by Username](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/findbyusername) | 演示如何使用Spring Session通过用户名查找会话。 | [Find by Username](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/findbyusername.html) |
| 多用户会话管理 | 演示如何使用Spring Session同时管理多个浏览器会话（例如Google帐户）。 | [Manage Multiple Users Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/users.html) |
| [WebSocket](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/websocket) | 演示在WebSockets中如何使用Spring Session与。 | [WebSocket Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/websocket.html) |
| [Mongo](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/mongo) | 演示在Monogo程序中如何使用Spring Session。 | [Mongo Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/mongo.html) |
| [Hazelcast](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/hazelcast) | 演示在Hazelcast程序中如何使用Spring Session。 | TBD |
| [Hazelcast Spring](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/hazelcast-spring) | 演示在基于Spring Security的Hazelcast程序中如何使用Spring Session。 | [Hazelcast Spring Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/hazelcast-spring.html) |
| [HttpSession JDBC](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/httpsession-jdbc) | 演示如何使用Spring Session替换HttpSession,将关系数据库作为Session存储容器。 | [HttpSession JDBC Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/httpsession-jdbc.html) |
| [HttpSession JDBC XML](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/httpsession-jdbc-xml) | 演示Spring Session基于XML的配置方式替换Https session，将关系数据库作为Session存储容器 | [HttpSession JDBC XML Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/httpsession-jdbc-xml.html) |
| [HttpSession JDBC Spring Boot](https://github.com/spring-projects/spring-session/tree/1.3.1.RELEASE/samples/httpsession-jdbc-boot) | 演示在Spring boot应用中使用Spring Session替换 Https session，将关系数据库作为Session存储容器 | [HttpSession JDBC Spring Boot Guide](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/guides/httpsession-jdbc-boot.html) |

# 4.HttpSession的集成

Spring Session支持与HttpSession的透明集成。 这意味着开发人员可以使用Spring Session支持的实现来切换HttpSession实现。

## 4.1为什么讨论Spring Session&HttpSession？

我们已经提到Spring Session支持与HttpSession的透明集成，但是这对我们有什么好处呢？

* 集群Session支持 - Spring Session使得集群Session非常简单，这使得集群Session的解决方案不依赖于应用程序容器特定的解决方案。
* 多个浏览器会话支持 - Spring Session支持在单个浏览器实例中管理多个用户的会话（即与Google类似的多个经过身份验证的帐户）。
* RESTful API支持 - Spring Session允许在Http请求头中提供会话ID以使用RESTful API

## 4.2基于Redis的HttpSession实现

Spring Session通过添加Servlet过滤器来实现替换HttpSession的，可以通过两种方式配置过滤器：

* 基于java的配置方式
* 基于XML的配置方式

### 4.2.1基于java的配置方式

本节介绍如何使用Java的配置方式来实现基于Redis的HttpSession。

注意：HttpSession Sample提供了一个关于如何使用Java配置集成Spring Session和HttpSession的工作示例。 您可以阅读下面的集成基本步骤，但是当您与自己的应用程序集成时，建议您遵循详细的HttpSession指南。

#### **Spring的java配置**

添加所需的依赖关系后，我们可以创建我们的Spring配置。 Spring配置负责创建一个使用Spring Session支持的实现替换HttpSession实现的Servlet过滤器。 添加以下Spring配置：

```
@EnableRedisHttpSession 1⃣
public class Config {

        @Bean
        public LettuceConnectionFactory connectionFactory() {
                return new LettuceConnectionFactory(); 2⃣
        }
}
```

1⃣@EnableRedisHttpSession注释创建一个名为springSessionRepositoryFilter的Spring Bean，该实例实现了Filter。 过滤器是负责替换由Spring Session支持的HttpSession实现的过程。 在这种情况下，Spring Session由Redis支持。

2⃣我们创建一个将Spring Session连接到Redis Server的RedisConnectionFactory。 我们配置默认端口为（6379）。有关配置，请参考Spring Data Redis的参考文档。

#### Java Servlet容器的初始化

我们的Spring Configuration创建了一个名为springSessionRepositoryFilter的Spring Bean，改Bean实现了Filter接口。 springSessionRepositoryFilter bean负责使用Spring Session支持的自定义实现来替换HttpSession。

为了使我们的过滤器能够做到这一点，Spring需要加载我们的Config配置类。 最后，我们需要确保我们的Servlet容器（即Tomcat）为每个请求使用我们的springSessionRepositoryFilter。 幸运的是，Spring Session提供了一个名为AbstractHttpSessionApplicationInitializer的实用程序类，这两个步骤非常简单。 你可以在下面找到一个例子：

src/main/java/sample/Initializer.java

```
public class Initializer extends AbstractHttpSessionApplicationInitializer { 1⃣

        public Initializer() {
                super(Config.class); 2⃣
        }
}
```

> 我们的类（Initializer）的名称并不重要。 重要的是我们扩展AbstractHttpSessionApplicationInitializer。

1⃣第一步是扩展AbstractHttpSessionApplicationInitializer。 这样可以确保springSessionRepositoryFilter针对每个请求都会在Servlet容器注册。

2⃣AbstractHttpSessionApplicationInitializer还提供了一种机制，可以确保Spring加载我们的Config。

### 4.2.2基于XML的配置方式

本节介绍通过XML的配置方式来实现基于Redis的HttpSession。

> HttpSession XML Sample提供了一个关于如何使用XML配置集成Spring Session和HttpSession的示例。 您可以阅读下面的集成基本步骤，但是当与您自己的应用程序集成时，建议您遵循详细的HttpSession XML指南。

#### Spring的XML 配置

添加所需的依赖关系后，我们可以创建我们的Spring配置。 Spring配置负责创建一个使用Spring Session支持的实现替换HttpSession实现的Servlet过滤器。 添加以下Spring配置：

src/main/webapp/WEB-INF/spring/session.xml

```
1⃣
<context:annotation-config/>
<bean class="org.springframework.session.data.redis.config.annotation.web.http.RedisHttpSessionConfiguration"/>

2⃣
<bean class="org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory"/>
```

1⃣我们使用&lt;context:annotation-config /&gt;和RedisHttpSessionConfiguration的组合，因为Spring Session还没有提供XML Namespace支持（参见gh-104）。 这将创建一个Spring Bean，名称为springSessionRepositoryFilter，该Bean实现Filter接口，是负责替换由Spring Session支持的HttpSession实现的过程。 在这种情况下，Spring Session由Redis支持。

2⃣我们创建一个将Spring Session连接到Redis Server的RedisConnectionFactory。 我们配置默认端口为（6379）。有关配置，请参考Spring Data Redis的参考文档。

#### **以XML方式配置Servlet容器的初始化**

我们的Spring Configuration创建了一个名为springSessionRepositoryFilter的Spring Bean，改Bean实现了Filter接口。 springSessionRepositoryFilter bean负责使用Spring Session支持的自定义实现来替换HttpSession。

为了使我们的过滤器能够实现这种功能，我们需要指示Spring加载我们的session.xml配置。 我们通过以下配置来做到这一点：

src/main/webapp/WEB-INF/web.xml

```
<context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>
        /WEB-INF/spring/*.xml
    </param-value>
</context-param>
<listener>
    <listener-class>
        org.springframework.web.context.ContextLoaderListener
    </listener-class>
</listener>
```

ContextLoaderListener读取contextConfigLocation指定的session.xml配置。

最后，我们需要确保我们的Servlet容器（即Tomcat）为每个请求使用我们的springSessionRepositoryFilter。 以下代码段是最后一步：

src/main/webapp/WEB-INF/web.xml

```
<filter>
    <filter-name>springSessionRepositoryFilter</filter-name>
    <filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
</filter>
<filter-mapping>
    <filter-name>springSessionRepositoryFilter</filter-name>
    <url-pattern>/*</url-pattern>
    <dispatcher>REQUEST</dispatcher>
    <dispatcher>ERROR</dispatcher>
</filter-mapping>
```

DelegatingFilterProxy将根据springSessionRepositoryFilter按名称查找一个Bean，并将其转换为Filter。 对于调用DelegatingFilterProxy的每个请求，都将将调用springSessionRepositoryFilter进行处理。

### 4.3 基于Pivotal GemFire的HttpSession实现 {#httpsession-gemfire}

当Pivotal GemFire与Spring Session一起使用时，Web应用程序的HttpSession可以由GemFire管理的集群实现来替代，并可使用Spring Session的API方便地访问。

使用GemFire管理Spring Sessions的两个最常见的拓扑结构包括：

* [Client-Server](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/#httpsession-gemfire-clientserver)

* [Peer-To-Peer \(P2P\)](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/#httpsession-gemfire-p2p)

此外，GemFire支持使用WAN功能的站点到站点复制。 配置和使用GemFire的WAN支持与Spring Session无关，超出了本文档的范围。 有关GemFire WAN功能的更多详细信息，请点击[此处](https://docs.spring.io/spring-data-gemfire/docs/current/reference/html/#bootstrap:gateway)。

### 4.3.1 GemFire Client-Server

当使用GemFire作为Spring Session中的提供程序时，Client-Server拓扑可能是更常见的配置首选项，因为与应用程序相比，GemFire服务器将具有显著不同且唯一的JVM堆需求。 使用Client-Server拓扑使应用程序能够独立地管理（例如复制）应用程序状态。

在Client-Server拓扑中，使用Spring Session的应用程序将打开到（远程）GemFire服务器集群的客户端缓存连接，以管理和提供对所有HttpSession状态的一致访问。

您可以使用以下任一配置Client-Server拓扑拓扑：

* 基于Java的配置
* 基于XML的配置

##### GemFire Client-Server基于java的配置 {#httpsession-gemfire-clientserver-java}

本节介绍如何使用GemFire的Client-Server拓扑来使用基于Java的配置来支持HttpSession。

> [HttpSession with GemFire \(Client-Server\) Sample](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/#samples)示例提供了一个关于如何使用Java配置来集成Spring Session和GemFire的工作示例。 您可以阅读下面的集成基本步骤，但是当您与自己的应用程序集成时，建议您遵循GemFire（Client-Server）指南中的详细HttpSession。

##### spring  java配置

添加所需的依赖关系和存储库声明后，我们可以创建我们的Spring配置。 Spring配置负责创建一个使用Spring Session和GemFire支持的实现替换HttpSession的Servlet过滤器。

添加以下Spring配置：

```
@EnableGemFireHttpSession(maxInactiveIntervalInSeconds = 30, poolName = "DEFAULT") 1⃣️
public class ClientConfig {

        static final long DEFAULT_WAIT_DURATION = TimeUnit.SECONDS.toMillis(20);

        static final CountDownLatch latch = new CountDownLatch(1);

        static final String DEFAULT_GEMFIRE_LOG_LEVEL = "warning";

        @Bean
        static PropertySourcesPlaceholderConfigurer propertySourcesPlaceholderConfigurer() {
                return new PropertySourcesPlaceholderConfigurer();
        }

        Properties gemfireProperties() { 
                Properties gemfireProperties = new Properties();
                gemfireProperties.setProperty("name", applicationName());
                gemfireProperties.setProperty("log-level", logLevel());
                return gemfireProperties;
        }

        String applicationName() {
                return "samples:httpsession-gemfire-clientserver:"
                        .concat(getClass().getSimpleName());
        }

        String logLevel() {
                return System.getProperty("sample.httpsession.gemfire.log-level",
                        DEFAULT_GEMFIRE_LOG_LEVEL);
        }

        @Bean
        ClientCacheFactoryBean gemfireCache(
                        @Value("${spring.session.data.gemfire.port:" + ServerConfig.SERVER_PORT + "}") int port) { 

                ClientCacheFactoryBean clientCacheFactory = new ClientCacheFactoryBean();

                clientCacheFactory.setClose(true);
                clientCacheFactory.setProperties(gemfireProperties());

                // GemFire Pool settings 
                clientCacheFactory.setKeepAlive(false);
                clientCacheFactory.setPingInterval(TimeUnit.SECONDS.toMillis(5));
                clientCacheFactory.setReadTimeout(2000); // 2 seconds
                clientCacheFactory.setRetryAttempts(1);
                clientCacheFactory.setSubscriptionEnabled(true);
                clientCacheFactory.setThreadLocalConnections(false);

                clientCacheFactory.setServers(Collections.singletonList(
                        newConnectionEndpoint(ServerConfig.SERVER_HOST, port)));

                return clientCacheFactory;
        }

        ConnectionEndpoint newConnectionEndpoint(String host, int port) {
                return new ConnectionEndpoint(host, port);
        }

        @Bean
        BeanPostProcessor gemfireCacheServerReadyBeanPostProcessor() { 
                return new BeanPostProcessor() {

                        public Object postProcessBeforeInitialization(Object bean, String beanName)
                                throws BeansException {

                                if ("gemfirePool".equals(beanName)) {
                                        ClientMembership.registerClientMembershipListener(
                                                new ClientMembershipListenerAdapter() {
                                                        @Override
                                                        public void memberJoined(ClientMembershipEvent event) {
                                                                latch.countDown();
                                                        }
                                                });
                                }

                                return bean;
                        }

                        public Object postProcessAfterInitialization(Object bean, String beanName)
                                throws BeansException {

                                if (bean instanceof Pool && "gemfirePool".equals(beanName)) {
                                        try {
                                                Assert.state(latch.await(DEFAULT_WAIT_DURATION, TimeUnit.MILLISECONDS),
                                                        String.format("GemFire Cache Server failed to start on host [%1$s] and port [%2$d]",
                                                                ServerConfig.SERVER_HOST, ServerConfig.SERVER_PORT));
                                        }
                                        catch (InterruptedException e) {
                                                Thread.currentThread().interrupt();
                                        }
                                }

                                return bean;
                        }
                };
        }
```

@EnableGemFireHttpSession注释创建一个名为springSessionRepositoryFilter的Spring bean，实现Filter。过滤器是用HttpSession替代由Spring Session和GemFire支持的实现。

接下来，我们注册一个Properties bean，允许我们使用GemFire的System属性来配置GemFire客户端缓存的某些方面。

我们使用属性来配置GemFire ClientCache的实例。

然后，我们配置一个客户端池池，以便在我们的Client / Server拓扑中与GemFire Server通信。在我们的配置中，我们已经使用了明智的设置超时，连接数等。此外，池已配置为直接连接到服务器。从PoolFactory API了解有关各种池配置设置的更多信息。

最后，我们包括一个Spring BeanPostProcessor来阻止客户端，直到我们的GemFire Server启动并运行，监听并接受客户端连接。

gemfireCacheServerReadyBeanPostProcessor是必要的，以便在测试期间以自动方式协调客户端和服务器，但在GemFire群集已经在运行的情况下（例如在生产中）是不必要的。

BeanPostProcessor使用GemFire ClientMembershipListener，当客户端已成功连接到服务器时，将会通知它们。一旦建立连接，监听器释放在PostProcessAfterInitialization回调中BeanPostProcessor将等待的锁存器（直到指定的超时），以阻止客户端。

> 在典型的GemFire部署中，集群中可能包含数百个GemFire数据节点（服务器），客户端更常见地连接到集群中运行的一个或多个GemFire定位器。 定位器将客户端的元数据传递给可用的服务器，负载以及哪些服务器具有客户端感兴趣的数据，这对于单跳直接数据访问特别重要。 在GemFire的用户指南中查看有关客户端/服务器拓扑的更多详细信息。
>
> 有关配置Spring Data GemFire的更多信息，请参阅参考指南。

@EnableGemFireHttpSession注释使开发人员能够使用以下属性来配置Spring Session和GemFire的特定方面：

maxInactiveIntervalInSeconds - 控制HttpSession空闲超时到期（默认为30分钟）。

regionName - 指定用于存储HttpSession状态的GemFire区域的名称（默认为“ClusteredSpringSessions”）。

clientRegionShort - 使用GemFire ClientRegionShortcut（默认为PROXY）指定GemFire的数据管理策略。此属性仅在配置客户端区域时使用。

poolName - 用于将客户端连接到服务器集群的专用GemFire池的名称。该属性仅在应用程序是GemFire缓存客户端时使用。默认为gemfirePool。

serverRegionShort - 使用GemFire RegionShortcut（默认为PARTITION）指定GemFire的数据管理策略。此属性仅在配置服务器区域时使用，或者在采用p2p拓扑时使用。

重要的是要注意，如果客户端区域是PROXY或CACHING\_PROXY，则GemFire客户端区域名称必须与服务器区域匹配相同的名称。如果用于存储Spring Sessions的客户端区域是LOCAL，则不需要匹配名称，但是请记住，您的会话状态不会传播到服务器，并且您失去了使用GemFire存储和管理分布式复制会话的所有好处集群中的状态信息。

serverRegionShort在客户机/服务器缓存配置中被忽略，仅在使用对等（P2P）拓扑，更具体地说是GemFire对等体缓存时适用。

#### 服务端配置

我们只涵盖了等式的一边。 我们还需要一个GemFire服务器端，我们的客户端可以与服务器进行通话并且将Session状态发送至服务器端，以进行管理。

在本示例中，GemFire服务端的Java配置如下：  
\`

```
    @EnableGemFireHttpSession(maxInactiveIntervalInSeconds = 30) 
public class ServerConfig {
    static final int SERVER_PORT = 12480;

    static final String DEFAULT_GEMFIRE_LOG_LEVEL = "warning";
    static final String SERVER_HOST = "localhost";

    @SuppressWarnings("resource")
    public static void main(String[] args) throws IOException { 5⃣️
            new AnnotationConfigApplicationContext(ServerConfig.class)
                    .registerShutdownHook();
    }

    @Bean
    static PropertySourcesPlaceholderConfigurer propertyPlaceholderConfigurer() {
            return new PropertySourcesPlaceholderConfigurer();
    }

    Properties gemfireProperties() { 2⃣️
            Properties gemfireProperties = new Properties();

            gemfireProperties.setProperty("name", applicationName());
            gemfireProperties.setProperty("mcast-port", "0");
            gemfireProperties.setProperty("log-level", logLevel());
            gemfireProperties.setProperty("jmx-manager", "true");
            gemfireProperties.setProperty("jmx-manager-start", "true");

            return gemfireProperties;
    }

    String applicationName() {
            return "samples:httpsession-gemfire-clientserver:"
                    .concat(getClass().getSimpleName());
    }

    String logLevel() {
            return System.getProperty("sample.httpsession.gemfire.log-level",
                    DEFAULT_GEMFIRE_LOG_LEVEL);
    }

    @Bean
    CacheFactoryBean gemfireCache() { 3⃣️
            CacheFactoryBean gemfireCache = new CacheFactoryBean();

            gemfireCache.setClose(true);
            gemfireCache.setProperties(gemfireProperties());

            return gemfireCache;
    }

    @Bean
    CacheServerFactoryBean gemfireCacheServer(Cache gemfireCache,
                    @Value("${spring.session.data.gemfire.port:" + SERVER_PORT + "}") int port) { 4⃣️

            CacheServerFactoryBean gemfireCacheServer = new CacheServerFactoryBean();

            gemfireCacheServer.setAutoStartup(true);
            gemfireCacheServer.setBindAddress(SERVER_HOST);
            gemfireCacheServer.setCache(gemfireCache);
            gemfireCacheServer.setHostNameForClients(SERVER_HOST);
            gemfireCacheServer.setMaxTimeBetweenPings(Long.valueOf(TimeUnit.SECONDS.toMillis(60)).intValue());
            gemfireCacheServer.setPort(port);

            return gemfireCacheServer;
    }
```

}  
\`

1⃣️在服务器端也使用@EnableGemFireHttpSession注解来配置Spring Session。 这确保了客户端和服务端的区域名称匹配（在此示例中，我们使用默认的“ClusteredSpringSessions”）。 我们还将Session的过期时间设置为30秒。 稍后我们将看到如何使用这个过期时间。

2⃣️接下来，我们使用GemFire系统属性配置GemFire服务器，这非常像我们的P2P示例中的配置。 为了使服务端保持独立，我们将mcast-port设置为0并且没有指定locator属性。GemFire服务端还允许一个使用JMX客户端（例如Gfsh）来连接，但是该JMX必须的系统属性必须是特定于GemFire的。

3⃣️然后，我们创建一个基于GemFire系统属性的GemFire对等缓存实例。

4⃣️我们还设置了在localhost上运行的GemFire CacheServer实例，监听端口12480，准备接受我们的客户端连接。

5⃣️最后，我们将一个main方法声明为从命令行启动作为运行GemFire Server的入口点。

Java Servlet容器初始化

我们的Spring Java配置创建了一个名为springSessionRepositoryFilter的Spring bean，该Bean实现了Filter接口。 springSessionRepositoryFilter bean负责使用基于GemFire支持的Spring Session来替换HttpSession。

为了使springSessionRepositoryFilter过滤器能够做到这一点，Spring需要加载我们的ClientConfig配置类。 还需要确保Servlet容器（即Tomcat）为每个请求使用springSessionRepositoryFilter。 幸运的是，Spring Session提供了一个名为AbstractHttpSessionApplicationInitializer的实用程序类，使这两个步骤都非常容易。

可以参考如下示例：

src/main/java/sample/Initializer.java

public class Initializer extends AbstractHttpSessionApplicationInitializer { 1⃣️

```
    public Initializer() {
            super(ClientConfig.class); 2⃣️
    }
```

}  
注意：我们的类（Initializer）的名称并不重要。 重要的是需要扩展AbstractHttpSessionApplicationInitializer类即可。  
1⃣️第一步是扩展AbstractHttpSessionApplicationInitializer类。 这确保了一个名为springSessionRepositoryFilter的Spring bean已经注册到我们的Servlet容器并应用于每个请求。

2⃣️AbstractHttpSessionApplicationInitializer还提供了一种便于Spring加载我们的ClientConfig的机制。

## 4.9 HttpSession & RESTful APIs

Spring session可以通过允许在标题中提供会话来使用RESTful API。

> REST示例提供了一个关于如何在REST应用程序中使用Spring Session来支持http请求头进行身份验证的工作示例。 您可以按照以下基本步骤进行集成，但在与自己的应用程序集成时，建议您遵循详细的REST指南。

### spring配置

添加所需的依赖关系后，我们可以创建我们的Spring配置。 Spring配置负责创建一个使用Spring Session支持的实现替换HttpSession实现的Servlet过滤器。 添加以下Spring配置：

```
@Configuration
@EnableRedisHttpSession 1⃣
public class HttpSessionConfig {

        @Bean
        public LettuceConnectionFactory connectionFactory() {
                return new LettuceConnectionFactory(); 2⃣
        }

        @Bean
        public HttpSessionStrategy httpSessionStrategy() {
                return new HeaderHttpSessionStrategy(); 3⃣
        }
}
```

1⃣@EnableRedisHttpSession注释创建一个名为springSessionRepositoryFilter的Spring Bean，该实例实现了Filter。 过滤器是负责替换由Spring Session支持的HttpSession实现的过程。 在这种情况下，Spring Session由Redis支持。

2⃣我们创建一个将Spring Session连接到Redis Server的RedisConnectionFactory。 我们配置默认端口为（6379）。有关配置，请参考Spring Data Redis的参考文档。

3⃣实现自定义Spring Session的HttpSession集成，使用HTTP请求来传输当前会话信息而不是Cookie。

### Servlet容器的初始化

我们的Spring Configuration创建了一个名为springSessionRepositoryFilter的Spring Bean，改Bean实现了Filter接口。 springSessionRepositoryFilter bean负责使用Spring Session支持的自定义实现来替换HttpSession。

为了使我们的过滤器能够做到这一点，Spring需要加载我们的Config类。 我们在Spring MvcInitializer中提供了如下配置：

src/main/java/sample/mvc/MvcInitializer.java

```
@Override
protected Class<?>[] getRootConfigClasses() {
    return new Class[] { SecurityConfig.class, HttpSessionConfig.class };
}
```

最后，我们需要确保我们的Servlet容器（即Tomcat）为每个请求使用我们的springSessionRepositoryFilter。 幸运的是，Spring Session提供了一个名为AbstractHttpSessionApplicationInitializer的实用程序类，使其非常简单。 只需使用默认构造函数扩展类，如下所示：

src/main/java/sample/Initializer.java

```
public class Initializer extends AbstractHttpSessionApplicationInitializer {

}
```

> 我们的类（Initializer）的名称并不重要。 重要的是我们扩展AbstractHttpSessionApplicationInitializer。

## 4.10 HttpSession & RESTful APIs

Spring Session通过声明SessionEventHttpSessionListenerAdapter将SessionDestroyedEvent和SessionCreatedEvent转换为HttpSessionEvent来支持HttpSessionListener。 要使用HttpSessionListener，您需要：

* 确保您的SessionRepository实现并配置为触发SessionDestroyedEvent和SessionCreatedEvent。
* 将SessionEventHttpSessionListenerAdapter配置为Spring bean。
* 将每个HttpSessionListener注入到SessionEventHttpSessionListenerAdapter中

如果您正在使用本文档中提到的HttpSession with Redis，那么您需要做的就是将每个HttpSessionListener注册为一个bean。 例如，假设您要支持Spring Security的并发控制，并且需要使用HttpSessionEventPublisher，您可以简单地将HttpSessionEventPublisher添加为一个bean。 在Java配置中，可能如下所示：

```
@Configuration
@EnableRedisHttpSession
public class RedisHttpSessionConfig {

        @Bean
        public HttpSessionEventPublisher httpSessionEventPublisher() {
                return new HttpSessionEventPublisher();
        }

        // ...
}
```

采用XML的配置方式如下：

```
<bean class="org.springframework.security.web.session.HttpSessionEventPublisher"/>
```

# 5.WebSocket的集成

### 5.1 为什么选择Spring Session & WebSockets？ {#websocket-why}

那么为什么在使用WebSockets时需要Spring Session呢？

考虑一个通过HTTP请求完成大部分工作的电子邮件应用程序。以及通过WebSocket API实现的聊天应用程序。 如果一个用户正在和某人进行积极的聊天，那么我们不应该让HttpSession超时，因为这样会导致很差的用户体验。 因此，这正是JSR-356解决的问题。

另一个问题是，根据JSR-356，如果HttpSession超时，则使用该HttpSession创建的任何WebSocket以及登陆认证的用户都应被强制关闭。 这意味着如果我们正在应用程序中聊天，如果没有操作HttpSession，那么我们也将被断开聊天对话！

## 5.2 WebSocket中应用Spring Session

[WebSocket Sample](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/#samples)提供了有关如何将Spring Session与WebSockets集成的示例。 您可以按照以下基本步骤进行集成，但是当与您自己的应用程序集成时，建议您遵循详细的“WebSocket指南”：

### 5.2.1 HttpSession集成

在使用WebSocket集成之前，您应该确保HttpSession正常工作。

### 5.2.2 Spring配置

在一个典型的Spring WebSocket应用程序中，用户将扩展AbstractWebSocketMessageBrokerConfigurer。 例如，配置可能如下所示：

```
@Configuration
@EnableScheduling
@EnableWebSocketMessageBroker
public class WebSocketConfig extends AbstractWebSocketMessageBrokerConfigurer {

        public void registerStompEndpoints(StompEndpointRegistry registry) {
                registry.addEndpoint("/messages").withSockJS();
        }

        @Override
        public void configureMessageBroker(MessageBrokerRegistry registry) {
                registry.enableSimpleBroker("/queue/", "/topic/");
                registry.setApplicationDestinationPrefixes("/app");
        }
}
```

我们可以轻松地更新您的配置以使用Spring Session WebSocket支持。 例如:

```
@Configuration
@EnableScheduling
@EnableWebSocketMessageBroker
public class WebSocketConfig
                extends AbstractSessionWebSocketMessageBrokerConfigurer<ExpiringSession> { 1⃣️

        protected void configureStompEndpoints(StompEndpointRegistry registry) { 2⃣️
                registry.addEndpoint("/messages").withSockJS();
        }

        public void configureMessageBroker(MessageBrokerRegistry registry) {
                registry.enableSimpleBroker("/queue/", "/topic/");
                registry.setApplicationDestinationPrefixes("/app");
        }
}
```

在WebSocket与Spring Session集成中，我们只需要改变两件事情：

1⃣️ WebSocket的配置累集成AbstractSessionWebSocketMessageBrokerConfigurer而不是AbstractWebSocketMessageBrokerConfigurer我们扩展

2⃣️ 重命名registerStompEndpoints方法来配置StompEndpoints

BackgroundSessionWebSocketMessageBrokerConfigurer在幕后做什么？

* WebSocketConnectHandlerDecoratorFactory作为WebSocketHandlerDecoratorFactory添加到WebSocketTransportRegistration。这样可以确保包含WebSocketSession的SessionConnectEvent被触发。当Spring Session终止时，WebSocketSession必须终止任何WebSocket连接。
* SessionRepositoryMessageInterceptor作为HandshakeInterceptor添加到每个StompWebSocketEndpointRegistration中。这样可以确保将Session添加到WebSocket属性，以便更新上次访问的时间。
* 将SessionRepositoryMessageInterceptor作为ChannelInterceptor添加到我们的入站ChannelRegistration中。这样可以确保每次收到入站邮件时，我们的Spring Session的上次访问时间都将被更新。
* WebSocketRegistryListener被创建为一个Spring Bean。这样可以确保我们将所有Session ID映射到相应的WebSocket连接。通过维护此映射，当Spring Session（HttpSession）终止时，我们可以关闭所有的WebSocket连接。

# 6.Spring Security的集成

Spring Session 支持与Spring Security的集成。

## 6.1 Spring Security"记住我"功能的支持

Spring Session提供了与Spring Security记住我功能的支持，这包括：

* 延长session的过期时间
* 确保session cookie 的过期时间为Integer.MAX\_VALUE。cookie过期时间被设置为最大可能的值，因为仅在创建session时设置cookie。 如果将cookie的过期时间与session的过期时间设置为相同的值，则当用户使用该session时，session将被更新，但是cookie的过期时间不会被更新，从而导致cookie的过期时间固定。

基于Java的配置方式将Spring Session集成到Spring Security中，请使用以下内容作为参考：

```
@Override
protected void configure(HttpSecurity http) throws Exception {
    http
        // ... additional configuration ...
        .rememberMe()
            .rememberMeServices(rememberMeServices());
}

@Bean
RememberMeServices rememberMeServices() {
    SpringSessionRememberMeServices rememberMeServices =
            new SpringSessionRememberMeServices();
    // optionally customize
    rememberMeServices.setAlwaysRemember(true);
    return rememberMeServices;
}
```

基于XML的配置方式如下：

```
<security:http>
    <!-- ... -->
    <security:form-login />
    <security:remember-me services-ref="rememberMeServices"/>
</security:http>

<bean id="rememberMeServices"
    class="org.springframework.session.security.web.authentication.SpringSessionRememberMeServices"
    p:alwaysRemember="true"/>
```

## 6.2 Spring Security对并发session的控制

Spring Session支持Spring Security的并发session的控制。这允许限制单个用户可以并发的活动会话数，但与默认的Spring Security支持不同，这也可以在集群环境中使用。 这通过提供Spring Security的SessionRegistry接口的自定义实现来实现。

当使用Spring Security的Java配置DSL时，可以通过SessionManagementConfigurer配置自定义SessionRegistry，如下所示：

```
@Configuration
public class SecurityConfiguration extends WebSecurityConfigurerAdapter {

        @Autowired
        FindByIndexNameSessionRepository<ExpiringSession> sessionRepository;

        @Override
        protected void configure(HttpSecurity http) throws Exception {
                http
                        // other config goes here...
                        .sessionManagement()
                                .maximumSessions(2)
                                .sessionRegistry(sessionRegistry());
        }

        @Bean
        SpringSessionBackedSessionRegistry sessionRegistry() {
                return new SpringSessionBackedSessionRegistry(this.sessionRepository);
        }
}
```

这假设您还配置了Spring Session来提供一个返回ExpiringSession实例的FindByIndexNameSessionRepository。

使用XML配置时，会看起来像这样：

```
<security:http>
    <!-- other config goes here... -->
    <security:session-management>
        <security:concurrency-control max-sessions="2" session-registry-ref="sessionRegistry"/>
    </security:session-management>
</security:http>

<bean id="sessionRegistry"
      class="org.springframework.session.security.SpringSessionBackedSessionRegistry">
    <constructor-arg ref="sessionRepository"/>
</bean>
```

这假设你的Spring Session SessionRegistry bean被称为sessionRegistry，它是所有SpringHttpSessionConfiguration子类使用的名称，除了用于MongoDB的名称之外：它被称为mongoSessionRepository。

## 6.3 局限

Spring Session实现的Spring Security的SessionRegistry接口不支持getAllPrincipals方法，因为这个信息无法使用Spring Session进行检索。 Spring Security不会调用此方法，因此这仅影响访问SessionRegistry本身的应用程序。

# 7.API文档

您可以在线浏览完整的[Javadoc](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/api/)。 关键API如下所述：

## 7.1 Session

session是key-value的集合，可以看作是简化的Map。

session的典型用法如下：

```
public class RepositoryDemo<S extends Session> {
    private SessionRepository<S> repository; 1⃣

    public void demo() {
        S toSave = this.repository.createSession(); 2⃣

        3⃣
        User rwinch = new User("rwinch");
        toSave.setAttribute(ATTR_USER, rwinch);

        this.repository.save(toSave); 4⃣

        S session = this.repository.getSession(toSave.getId()); 

        6⃣
        User user = session.getAttribute(ATTR_USER);5⃣
        assertThat(user).isEqualTo(rwinch);
    }

    // ... setter methods ...
}
```

1⃣创建一个泛型的SessionRepository实例，S代表Session的子类，泛型的具体类型通过SessionRepository来获取。

2⃣通过SessionRepository创建一个新的Session实例，将此实例赋值给泛型S声明的变量。

3⃣操作Session，这里我们将一个User实例保存到Session中。

4⃣保存Session，泛型S的作用就体现在这里. SessionRepository只允许保存使用相同SessionRepository创建或获取的Session实例。 这允许SessionRepository进行特定的优化（即仅写入已经改变的属性）。

5⃣从SessionRepository获取Session实例。

6⃣从Session中获取持久化的User，这里不需要强制类型转换。

## 7.2 ExpiringSession

ExpiresSession继承Session，扩展了与Session过期时间相关的属性。 如果程序不需要与Session过期时间进行交互，则推荐使用更简单的Session API。

ExpiringSession的典型用法如下：

```
public class ExpiringRepositoryDemo<S extends ExpiringSession> {
    private SessionRepository<S> repository; 1⃣

    public void demo() {
        S toSave = this.repository.createSession(); 2⃣
        // ...
        toSave.setMaxInactiveIntervalInSeconds(30); 3⃣

        this.repository.save(toSave); 4⃣

        S session = this.repository.getSession(toSave.getId()); 5⃣
        // ...
    }

    // ... setter methods ...
}
```

1⃣创建一个泛型的SessionRepository实例，S代表ExpiringSession的子类，泛型的具体类型通过SessionRepository来获取。

2⃣通过SessionRepository创建一个新的ExpiringSession实例，将此实例赋值给泛型S声明的变量。

3⃣操作Session，这里我们演示如何在Session过期之前更新Session的过期时间。

4⃣保存Session，泛型S的作用就体现在这里. SessionRepository只允许保存使用相同SessionRepository创建或获取的Session实例。 这允许SessionRepository进行特定的优化（即仅写入已经改变的属性）。当ExpiringSession被保存时，最后访问时间会自动更新。

5⃣从SessionRepository获取Session实例，如果Session已经过期，则结果为Null。

## 7.3 SessionRepository

SessionRepository负责创建、获取和持久化Session实例。

开发人员尽量避免直接与SessionRepository或Session进行交互。 相反，开发人员应该倾向于通过与HttpSession和WebSocket集成的方式来间接地与SessionRepository和Session进行交互。

## 7.4 FindByIndexNameSessionRepository

Spring Session中用于操作Session的最基本的API是SessionRepository。 SessionRepository力求简单，因此可以轻松提供具有基本功能的其他实现。

一些SessionRepository实现也可以选择实现FindByIndexNameSessionRepository。 例如，Spring的Redis支持，就实现了FindByIndexNameSessionRepository接口。

FindByIndexNameSessionRepository添加一个方法来查找特定用户的所有Session。 这是通过使用FindByIndexNameSessionRepository.PRINCIPAL\_NAME\_INDEX\_NAME为key的会话属性填充用户名来完成的。 开发人员负责添加属性，因为Spring Session不知道正在使用的身份验证机制。 可以参考下面的例子：

```
String username = "username";
this.session.setAttribute(
        FindByIndexNameSessionRepository.PRINCIPAL_NAME_INDEX_NAME, username);
```

> FindByIndexNameSessionRepository的一些实现将提供钩子来自动索引其他会话属性。 例如，许多实现将自动确保当前的Spring Security用户名使用索引名称FindByIndexNameSessionRepository.PRINCIPAL\_NAME\_INDEX\_NAME进行索引。

Session被索引后，可以通过如下方式找到：

```
String username = "username";
Map<String, Session> sessionIdToSession = this.sessionRepository
        .findByIndexNameAndIndexValue(
                FindByIndexNameSessionRepository.PRINCIPAL_NAME_INDEX_NAME,
                username);
```

## 7.5 EnableSpringHttpSession

@EnableSpringHttpSession注释可以添加到@Configuration注解的配置类上，用于暴露一个名称为“springSessionRepositoryFilter“

的SessionRepositoryFilter。 为了使用这个注释，必须提供SessionRepository bean。 例如：

```
@EnableSpringHttpSession
@Configuration
public class SpringHttpSessionConfig {
        @Bean
        public MapSessionRepository sessionRepository() {
                return new MapSessionRepository();
        }
}
```

注意，在Spring Session的基础架构中并没有提供开箱即用的Session过期配置。 这是因为Session的过期时间高度依赖于具体的实现。 这意味着如果您需要清理已过期的Session，需要自己实现清理过期的Session。

## 7.6 edisOperationsSessionRepository

RedisOperationsSessionRepository是基于Spring Data的RedisOperations实现的SessionRepository。 在Web环境中，这通常与SessionRepositoryFilter结合使用。 该实现通过SessionMessageListener支持SessionDestroyedEvent和SessionCreatedEvent。

### 7.6.1 初始化一个RedisOperationsSessionRepository实例

```
LettuceConnectionFactory factory = new LettuceConnectionFactory();
SessionRepository<? extends ExpiringSession> repository = new RedisOperationsSessionRepository(
        factory);
```

有关如何创建RedisConnectionFactory的其他信息，请参考Spring Data Redis参考。

### 7.6.2 EnableRedisHttpSession

在Web环境中，创建RedisOperationsSessionRepository的最简单方法是使用@EnableRedisHttpSession注解。 [Samples and Guides](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/#samples)中可以找到完整的示例用法，您可以使用以下属性来自定义配置：

* maxInactiveIntervalInSeconds - Session过期时间

* redisNamespace - 允许为Session配置应用程序特定的命名空间。 Redis的Key和channel ID将以spring:session:&lt;redisNamespace&gt;：前缀开头。

* redisFlushMode - 允许指定何时将数据写入Redis。 默认情况下，只有在SessionRepository上调用save时，才将数据写入Redis。 RedisFlushMode.IMMEDIATE模式将尽快将数据写入Redis。

##### 自定义RedisSerializer {#custom-redisserializer}

通过创建一个名为springSessionDefaultRedisSerializer，并且实现RedisSerializer &lt;Object&gt;接口的Bean来自定义序列化。

### 7.6.3 Redis TaskExecutor

RedisOperationsSessionRepository使用RedisMessageListenerContainer从redis接收事件。 您可以通过创建名为springSessionRedisTaskExecutor的Bean和/或springSessionRedisSubscriptionExecutor来自定义这些事件的分派方式。 有关配置redis任务执行程序的更多详细信息，请参见[此处](https://docs.spring.io/spring-data-redis/docs/current/reference/html/#redis:pubsub:subscribe:containers)。

### 7.6.4 存储细节

以下部分概述了Redis如何针对每个操作进行更新。 创建新Session的示例如下。 后续部分将详细介绍。

```
HMSET spring:session:sessions:33fdd1b6-b496-4b33-9f7d-df96679d32fe creationTime 1404360000000 \
    maxInactiveInterval 1800 \
    lastAccessedTime 1404360000000 \
    sessionAttr:attrName someAttrValue \
    sessionAttr2:attrName someAttrValue2
EXPIRE spring:session:sessions:33fdd1b6-b496-4b33-9f7d-df96679d32fe 2100
APPEND spring:session:sessions:expires:33fdd1b6-b496-4b33-9f7d-df96679d32fe ""
EXPIRE spring:session:sessions:expires:33fdd1b6-b496-4b33-9f7d-df96679d32fe 1800
SADD spring:session:expirations:1439245080000 expires:33fdd1b6-b496-4b33-9f7d-df96679d32fe
EXPIRE spring:session:expirations1439245080000 2100
```

#### 存储Session

每个Session都以Hash形式存储在Redis中。 使用HMSET命令设置和更新每个Session。 下面可以看到每个Session如何存储的一个例子。

```
HMSET spring:session:sessions:33fdd1b6-b496-4b33-9f7d-df96679d32fe creationTime 1404360000000 \
    maxInactiveInterval 1800 \
    lastAccessedTime 1404360000000 \
    sessionAttr:attrName someAttrValue \
    sessionAttr2:attrName someAttrValue2
```

在此示例中，Session的各部分分别为：

sessionid是：33fdd1b6-b496-4b33-9f7d-df96679d32fe

session的创建时间是1404360000000，这是一个从1/1/1970 GMT开始的一个时间戳。

session的过期时间是1800秒（30分钟）

session的最后访问时间是1404360000000，这是一个从1/1/1970 GMT开始的一个时间戳。

session有两个属性。第一个属性的名称是"attrName"，值是"someAttrValue"，第二个属性的名称是"attrName2"，值是"someAttrValue2"。

##### Session优化写入值

由RedisOperationsSessionRepository管理的Session实例跟踪已更改的属性，并只更新这些属性。 这意味着如果一个属性被写入一次并且读取很多次，我们只需要写入该属性一次。 例如，假设前面的会话属性“sessionAttr2”已更新。 保存后将执行以下操作：

```
HMSET spring:session:sessions:33fdd1b6-b496-4b33-9f7d-df96679d32fe sessionAttr:attrName2 newValue
```

##### Session过期时间 {#api-redisoperationssessionrepository-expiration}

每个Session的过期时间用ExpiringSession.getMaxInactiveInterval\(\)来获取，通过EXPIRE命令来更新过期时间。 例如：

```
EXPIRE spring:session:sessions:33fdd1b6-b496-4b33-9f7d-df96679d32fe 2100
```

注意Session的实际过期时间比设置的过期时间延迟5分钟。 这是必要的，以便在Session过期后可以访问Session的值。 这样做的目的是要确保Session被清理干净，但只有在我们执行任何必要的处理之后再执行清理。

> SessionRepository.getSession\(String\)方法确保了不会获取过期的Session，这意味着我们在使用一个session时不用检查Sessionde过期时间。

Spring Session依赖于Redis的delete和[keyspace notifications](http://redis.io/topics/notifications)，分别触发SessionDeletedEvent和SessionExpiredEvent事件。 SessionDeleEvent或SessionExpiredEvent可以确保与Session关联的资源被清除。 例如，当使用Spring Session与WebSocket集成时，Redis过期或delete事件会导致与Session关联的任何WebSocket连接关闭。

Session本身不直接跟踪过期时间，因为这意味着Session数据将不再可用。 而是使用特殊的Session过期Key。 在我们的例子中，过期Key是：

```
APPEND spring:session:sessions:expires:33fdd1b6-b496-4b33-9f7d-df96679d32fe ""
EXPIRE spring:session:sessions:expires:33fdd1b6-b496-4b33-9f7d-df96679d32fe 1800
```

当Session过期时，Redis的keyspace notification（键空间通知）间通知会通知查找对应的Session，并触发一个SessionDestroyedEvent事件。

依靠Redis的expired有一个问题，就是Redis不保证expired的事件会被触发。具体来说，Redis用于清除过期Session的后台任务是低优先级任务，可能不会触发Session过期。有关其他详细信息，请参阅Redis文档中的expired事件部分。

为了避免 expired事件不能保证被触发的事实，我们可以确保在Session即将过期时访问每个Session 的key。这意味着如果TTL在该key上过期，当我们尝试访问它的key时，Redis将删除该key并触发过期的事件。

因此，每个Session也会记录即将过期的最近时间。这允许后台任务访问即将的过期会话，以确保以更准确的触发Redis过期事件。例如：

```
SADD spring:session:expirations:1439245080000 expires:33fdd1b6-b496-4b33-9f7d-df96679d32fe
EXPIRE spring:session:expirations1439245080000 2100
```

> 在某些情况下，我们没有明确删除key，这是因为可能存在竞争条件导致key被误判为过期。 Redis没有使用分布式锁（这会影响的性能），因此无法保证过期mapping的一致性。 通过简单的访问key的方式，我们确保该key只有在该key的TTL过期时才被删除。

### 7.6.5 SessionDeletedEvent和SessionExpiredEvent事件

SessionDeletedEvent和SessionExpiredEvent都是SessionDestroyedEvent事件的两种类型。

RedisOperationsSessionRepository支持在Session被删除时触发SessionDeletedEvent，或者在Session过期时触发SessionExpiredEvent事件。 这将确保与Session相关的资源被正确清理。

例如，当与WebSockets集成时，SessionDestroyedEvent负责关闭任何活动的WebSocket连接。

通过Redis Keyspace的事件监听器SessionMessageListener可以触发SessionDeletedEvent或SessionExpiredEvent事件。 为了使其工作，需要启用Generic命令和Expired事件的Redis Keyspace事件。 例如：

```
redis-cli config set notify-keyspace-events Egx
```

如果使用@EnableRedisHttpSession注解，则会自动启动SessionMessageListener监听器并触发必要的Redis Keyspace事件。 但是，在安全的Redis环境中，config命令被禁用。 这意味着Spring Session无法为您配置Redis Keyspace事件。 要禁用自动配置，请将ConfigureRedisAction.NO\_OP添加为一个bean。

例如，Java Configuration可以使用以下内容：

```
@Bean
public static ConfigureRedisAction configureRedisAction() {
    return ConfigureRedisAction.NO_OP;
}
```

XML配置如下：

```
<util:constant static-field="org.springframework.session.data.redis.config.ConfigureRedisAction.NO_OP"/>
```

### 7.6.6 SessionCreatedEvent事件

当Session创建时，将session:channel:created:33fdd1b6-b496-4b33-9f7d-df96679d32fe发送到Redis，其中33fdd1b6-b496-4b33-9f7d-df96679d32fe是Session ID。 事件体就是创建的会话。

如果注册了MessageListener（默认），则RedisOperationsSessionRepository会将Redis消息转换为SessionCreatedEvent。

### 7.6.7 查看Redis中的Session

安装redis-cli后，可以使用redis-cli查看Redis中的值。 例如，在终端中输入以下内容：

```
$ redis-cli
redis 127.0.0.1:6379> keys *
1) "spring:session:sessions:4fc39ce3-63b3-4e17-b1c4-5e1ed96fb021" 1⃣
2) "spring:session:expirations:1418772300000" 2⃣
```

1⃣该key的后缀是Spring Session的会话标识符。

2⃣此key包含的所有会话ID在1418772300000时被删除。

您还可以查看每个Session的属性。

```
redis 127.0.0.1:6379> hkeys spring:session:sessions:4fc39ce3-63b3-4e17-b1c4-5e1ed96fb021
1) "lastAccessedTime"
2) "creationTime"
3) "maxInactiveInterval"
4) "sessionAttr:username"
redis 127.0.0.1:6379> hget spring:session:sessions:4fc39ce3-63b3-4e17-b1c4-5e1ed96fb021 sessionAttr:username
"\xac\xed\x00\x05t\x00\x03rob"
```

## 7.7 GemFireOperationsSessionRepository

GemFireOperationsSessionRepository是使用Spring Data的GemFireOperationsSessionRepository实现的SessionRepository。 在Web环境中，这通常与SessionRepositoryFilter结合使用。 该实现通过SessionMessageListener支持SessionDestroyedEvent和SessionCreatedEvent。

### 7.7.1 GemFire使用索引

关于如何正确定义索引，来提升GemFire的性能超出了本文档的范围，但重要的是要认识到Spring Session Data GemFire可以有效地创建和使用索引来查询和查找会话。

开箱即用，Spring Session GemFire在主体名称上创建1个哈希类型的索引。 查找主体名称的策略有两种不同的表现。 第一个策略是名为FindByIndexNameSessionRepository.PRINCIPAL\_NAME\_INDEX\_NAME的会话属性的值将被索引到相同的索引名称。 例如：

```
String indexName = FindByIndexNameSessionRepository.PRINCIPAL_NAME_INDEX_NAME;
session.setAttribute(indexName, username);
Map<String, ExpiringSession> idToSessions = sessionRepository
        .findByIndexNameAndIndexValue(indexName, username);
```

## 7.7.2 GemFire & Spring Security使用索引

或者，Spring Session Data GemFire将Spring Security的当前`Authentication#getName()`映射到索引FindByIndexNameSessionRepository.PRINCIPAL\_NAME\_INDEX\_NAME。 例如，如果您使用的是Spring Security，可以使用以下方式查找当前用户的Session：

```
SecurityContext context = SecurityContextHolder.getContext();
Authentication authentication = context.getAuthentication();
String indexName = FindByIndexNameSessionRepository.PRINCIPAL_NAME_INDEX_NAME;
Map<String, ExpiringSession> idToSessions = sessionRepository
        .findByIndexNameAndIndexValue(indexName, authentication.getName());
```

## 7.7.3 GemFire使用自定义索引

这使开发人员能够以编程方式使用GemFireOperationsSessionRepository来查询和查找具有给定主体名称的所有Session。

此外，当开发人员识别出应该由GemFire索引的一个或多个命名的Session属性时，Spring Session Data GemFire将在实现Session的Map类型属性（即任意任意Session属性）上创建一个基于范围的索引。

可以使用@EnableGemFireHttpSession注解中的indexableSessionAttributes属性指定索引的会话属性。 当启用由GemFire支持的Spring Session时，开发人员将此注释添加到其Spring应用程序@Configuration类中。

例如，以下配置：

```
@EnableGemFireHttpSession(indexableSessionAttributes = { "name1", "name2", "name3" })
public class GemFireHttpSessionConfig {
        // ...
}
```

将允许使用以下内容搜索会话：

```
String indexName = "name1";
session.setAttribute(indexName, attrValue);
Map<String, ExpiringSession> idToSessions = sessionRepository
        .findByIndexNameAndIndexValue(indexName, attrValue);
```

> 只有在@EnableGemFireHttpSession注解的indexableSessionAttributes属性中标识的会话属性名称将定义索引。 所有其他会话属性将不被索引。

注意， 存储在可索引的Session属性中的任何值必须实现java.lang.Comparable &lt;T&gt;接口。 如果这些对象值不实现Comparable接口，那么当为具有持久Session数据的区域定义索引时，或者当在运行时尝试将可索引的Session属性分配给不可比较的值时，GemFire将在启动时抛出错误，并且将Session保存到GemFire。

> 没有索引的任何Session属性可以存储非可比较值。

要了解有关GemFire基于范围的索引的更多信息，请参阅在映射字段上创建索引。

要了解有关GemFire索引的更多信息，请参阅使用索引。

## 7.8 MapSessionRepository

MapSessionRepository允许在Map中持久化ExpiringSession，其中的key是ExpiresSession id，值为ExpiresSession。 该实现可以与ConcurrentHashMap一起用作测试或是一种约定。 或者，它可以与分布式Map实现一起使用。 例如，它可以与Hazelcast一起使用。

### 7.8.1 初始化MapSessionRepository

创建MapSessionRepository的示例很简单：

```
SessionRepository<? extends ExpiringSession> repository = new MapSessionRepository();
```

### 7.8.2 Spring Session和 Hazlecast

[Hazelcast Sample](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/#samples)是一个完整的应用程序，演示如何使用带有Hazelcast的Spring Session。

要运行它，请使用以下命令：

```
./gradlew :samples:hazelcast:tomcatRun
```

[Hazelcast Spring Sample](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/#samples)是一个完整的应用程序，演示了如何使用Spring Session与Hazelcast和Spring Security集成。

它包括Hazelcast MapListener实现，支持触发SessionCreatedEvent，SessionDeletedEvent和SessionExpiredEvent事件。

要运行它，请使用以下命令：

```
./gradlew :samples:hazelcast-spring:tomcatRun
```

## 7.9 JdbcOperationsSessionRepository

JdbcOperationsSessionRepository是一个SessionRepository实现，它使用Spring的JdbcOperations在关系数据库中存储Session。 在Web环境中，这通常与SessionRepositoryFilter结合使用。 请注意，此实现不支持发布session事件。

### 7.9.1 初始化JdbcOperationsSessionRepository实例

如何创建JdbcOperationsSessionRepository实例的典型示例如下所示：

```
JdbcTemplate jdbcTemplate = new JdbcTemplate();

// ... configure JdbcTemplate ...

PlatformTransactionManager transactionManager = new DataSourceTransactionManager();

// ... configure transactionManager ...

SessionRepository<? extends ExpiringSession> repository =
        new JdbcOperationsSessionRepository(jdbcTemplate, transactionManager);
```

有关如何创建和配置JdbcTemplate和PlatformTransactionManager的其他信息，请参阅[Spring Framework参考文档](https://docs.spring.io/spring/docs/current/spring-framework-reference/html/spring-data-tier.html)。

### 7.9.2 EnableJdbcHttpSession

在Web环境中，创建JdbcOperationsSessionRepository实例的最简单方法是使用@EnableJdbcHttpSession注解。 [Samples and Guides \(Start Here\)](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/#samples)可以找到完整的用法。您可以使用以下属性来自定义配置：

* tableName - Spring Session用于存储会话的数据库表的名称
* maxInactiveIntervalInSeconds - session的过期时间

##### 自定义LobHandler

您可以通过创建一个实现LobHandler接口、名称为springSessionLobHandler的Bean，来实现自定义BLOB处理。

##### 自定义ConversionService

您可以通过提供ConversionService实例来自定义session的序列化和反序列化机制。 在典型的Spring环境中时，默认的ConversionService Bean（名为conversionService）将被自动引用并用于序列化和反序列化。 但是，您可以通过提供一个名为springSessionConversionService的Bean覆盖默认的ConversionService。

### 7.9.3 存储细节

默认情况下，JdbcOperationsSessionRepository使用SPRING\_SESSION和SPRING\_SESSION\_ATTRIBUTES表来存储会话。 请注意，表名可以按照前面介绍的方式进行定制。 在这种情况下，用于存储属性的表将使用提供的表名命名，后缀为\_ATTRIBUTES。 如果需要进一步的自定义，则可以使用set \* Query setter方法来定制存储库使用的SQL查询。 在这种情况下，您需要手动配置sessionRepository bean。

由于各种数据库供应商之间的差异，特别是在存储二进制数据时，请确保使用特定于您的数据库的SQL脚本。 大多数主要数据库供应商的脚本打包为org / springframework / session / jdbc / schema - \*。sql，其中\*是目标数据库类型。

例如，使用PostgreSQL数据库，您将使用以下架构脚本：

```
CREATE TABLE SPRING_SESSION (
        SESSION_ID CHAR(36) NOT NULL,
        CREATION_TIME BIGINT NOT NULL,
        LAST_ACCESS_TIME BIGINT NOT NULL,
        MAX_INACTIVE_INTERVAL INT NOT NULL,
        PRINCIPAL_NAME VARCHAR(100),
        CONSTRAINT SPRING_SESSION_PK PRIMARY KEY (SESSION_ID)
);

CREATE INDEX SPRING_SESSION_IX1 ON SPRING_SESSION (LAST_ACCESS_TIME);

CREATE TABLE SPRING_SESSION_ATTRIBUTES (
        SESSION_ID CHAR(36) NOT NULL,
        ATTRIBUTE_NAME VARCHAR(200) NOT NULL,
        ATTRIBUTE_BYTES BYTEA NOT NULL,
        CONSTRAINT SPRING_SESSION_ATTRIBUTES_PK PRIMARY KEY (SESSION_ID, ATTRIBUTE_NAME),
        CONSTRAINT SPRING_SESSION_ATTRIBUTES_FK FOREIGN KEY (SESSION_ID) REFERENCES SPRING_SESSION(SESSION_ID) ON DELETE CASCADE
);

CREATE INDEX SPRING_SESSION_ATTRIBUTES_IX1 ON SPRING_SESSION_ATTRIBUTES (SESSION_ID);
```

MYSQL数据库如下：

```
CREATE TABLE SPRING_SESSION (
        SESSION_ID CHAR(36) NOT NULL,
        CREATION_TIME BIGINT NOT NULL,
        LAST_ACCESS_TIME BIGINT NOT NULL,
        MAX_INACTIVE_INTERVAL INT NOT NULL,
        PRINCIPAL_NAME VARCHAR(100),
        CONSTRAINT SPRING_SESSION_PK PRIMARY KEY (SESSION_ID)
) ENGINE=InnoDB;

CREATE INDEX SPRING_SESSION_IX1 ON SPRING_SESSION (LAST_ACCESS_TIME);

CREATE TABLE SPRING_SESSION_ATTRIBUTES (
        SESSION_ID CHAR(36) NOT NULL,
        ATTRIBUTE_NAME VARCHAR(200) NOT NULL,
        ATTRIBUTE_BYTES BLOB NOT NULL,
        CONSTRAINT SPRING_SESSION_ATTRIBUTES_PK PRIMARY KEY (SESSION_ID, ATTRIBUTE_NAME),
        CONSTRAINT SPRING_SESSION_ATTRIBUTES_FK FOREIGN KEY (SESSION_ID) REFERENCES SPRING_SESSION(SESSION_ID) ON DELETE CASCADE
) ENGINE=InnoDB;

CREATE INDEX SPRING_SESSION_ATTRIBUTES_IX1 ON SPRING_SESSION_ATTRIBUTES (SESSION_ID);
```

### 7.9.4 事务管理

JdbcOperationsSessionRepository中的所有JDBC操作都以事务方式执行。 事务的传播为REQUIRES\_NEW，以避免对现有事务的干扰（例如，在已经参与只读事务的线程中执行保存操作）。

## 7.10 HazelcastSessionRepository

# 8.Spring Session社区

我们欢迎您成为我们社区的一分子。 请在下面找到关于Spring Session的其他信息。

## 8.1 支持

您可以在StackOverflow上提出问题来获得帮助，提问地址是[StackOverflow with the tag spring-session](https://stackoverflow.com/questions/tagged/spring-session)。 同样，我们鼓励通过回答StackOverflow上的问题来帮助别人。

## 8.2 源码

Spring Session源码的地址是：

[https://github.com/spring-projects/spring-session/](https://github.com/spring-projects/spring-session/)

## 8.3 问题跟踪

通过[https://github.com/spring-projects/spring-session/issues](https://github.com/spring-projects/spring-session/issues)跟踪github上的问题。

## 8.4 贡献

我们很感激您[Pull Requests](https://help.github.com/articles/using-pull-requests/)。

## 8.5 License

Spring Session的开源许可证是基于[Apache 2.0 license](https://www.apache.org/licenses/LICENSE-2.0.html)。

## 8.6 社区扩展

[Spring Session OrientDB](https://github.com/maseev/spring-session-orientdb)[Spring Session Infinispan](http://infinispan.org/docs/dev/user_guide/user_guide.html#externalizing_session_using_spring_session)

# 9.最低版本要求

Spring Session的最低要求是：

* Java 5+
* 如果您正在运行Servlet容器（非必需），则Servlet 2.5+
* 如果您使用其他Spring库（非必需），则所需的最低版本为Spring 3.2.14。 当我们针对Spring 3.2.x重新运行所有单元测试时，建议尽可能使用最新的Spring 4.x版本。
* @EnableRedisHttpSession需要Redis 2.8+。 这对于支持Session Expiration是必要的。

> 在核心Spring Session中，只需要对commons-logging的依赖。 有关没有任何其他Spring依赖的Spring Session的示例，请参阅hazelcast示例应用程序。



