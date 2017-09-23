#### GemFire Client-Server基于XML的配置

本节介绍如何使用XML的配置方式来配置基于GemFire的Client-Server拓扑的HttpSession。

> [HttpSession with GemFire \(Client-Server\) using XML Sample](https://docs.spring.io/spring-session/docs/1.3.1.RELEASE/reference/html5/#samples)提供了一个关于如何使用基于GemFire实现的Spring Session来替换HttpSession的工作示例。 您可以阅读下面的集成基本步骤，但是当与您自己的应用程序集成时，您可以使用XML Guide与GemFire（Client-Server）一起使用详细的HttpSession。

##### Spring的XML配置 {#httpsession-spring-xml-configuration}

添加所需的依赖关系和存储库声明后，我们可以创建我们的Spring配置。 Spring配置负责创建一个使用Spring Session替换HttpSession的Servlet过滤器。

添加以下Spring配置：

```
        <context:annotation-config/>


        <context:property-placeholder location="classpath:META-INF/spring/application.properties"/>


        <bean class="sample.GemFireCacheServerReadyBeanPostProcessor"/>


        <util:properties id="gemfireProperties">
                <prop key="log-level">${sample.httpsession.gemfire.log-level:warning}</prop>
        </util:properties>


        <gfe:client-cache properties-ref="gemfireProperties" pool-name="gemfirePool"/>


        <gfe:pool keep-alive="false"
              ping-interval="5000"
              read-timeout="5000"
              retry-attempts="1"
              subscription-enabled="true"
              thread-local-connections="false">
                <gfe:server host="${application.gemfire.client-server.host}"
                    port="${spring.session.data.gemfire.port:${application.gemfire.client-server.port}}"/>
        </gfe:pool>


        <bean class="org.springframework.session.data.gemfire.config.annotation.web.http.GemFireHttpSessionConfiguration"
                  p:maxInactiveIntervalInSeconds="30" p:poolName="DEFAULT"/>
```

使用&lt;context：annotation-config /&gt;元素启用Spring注释配置支持，以便在Spring配置中声明的任何使用Spring支持的Spring或Standard Java注释的Spring bean都将被正确配置。

META-INF / spring / application.properties文件与PropertySourcesPlaceholderConfigurer bean一起使用，以将Spring XML配置元数据中的占位符替换为approrpriate属性值。

然后注册“GemFireCacheSeverReadyBeanPostProcessor”，以确定指定主机/端口上的GemFire Server是否正在运行并监听客户端连接，阻止客户端启动，直到服务器可用并准备就绪。

接下来，我们包括一个Properties bean，以使用GemFire的系统属性来配置GemFire客户端缓存的某些方面。在这种情况下，我们只是从应用程序特定的System属性设置GemFire的日志级别，如果未指定，则默认为警告。

然后我们创建一个使用我们的gemfireProperties初始化的GemFire ClientCache实例。

我们配置一个客户端池池，以与客户端/服务器拓扑中的GemFire服务器进行通信。在我们的配置中，我们使用明智的设置超时，连接数等。此外，我们的池已配置为直接连接到服务器。

最后，注册了GemFireHttpSessionConfiguration以启用Spring Session功能。

> 在典型的GemFire部署中，集群中可能包含数百个GemFire数据节点（服务器），客户端更常见地连接到集群中运行的一个或多个GemFire定位器。 定位器将客户端的元数据传递给可用的服务器，负载以及哪些服务器具有客户端感兴趣的数据，这对于单跳直接数据访问特别重要。 在GemFire的用户指南中查看有关客户端/服务器拓扑的更多详细信息。
>
> 有关配置Spring Data GemFire的更多信息，请参阅参考指南。

##### 服务端配置

我们只涵盖了方程的一边。 我们还需要一个GemFire服务器，我们的客户端可以将会话状态信息与服务器通信并发送到管理中。

在本示例中，我们将使用以下GemFire Server Java配置：

```
        <context:annotation-config/>


        <context:property-placeholder location="classpath:META-INF/spring/application.properties"/>


        <util:properties id="gemfireProperties">
                <prop key="name">GemFireClientServerHttpSessionXmlSample</prop>
                <prop key="mcast-port">0</prop>
                <prop key="log-level">${sample.httpsession.gemfire.log-level:warning}</prop>
                <prop key="jmx-manager">true</prop>
                <prop key="jmx-manager-start">true</prop>
        </util:properties>


        <gfe:cache properties-ref="gemfireProperties"/>


        <gfe:cache-server auto-startup="true"
                      bind-address="${application.gemfire.client-server.host}"
                      host-name-for-clients="${application.gemfire.client-server.host}"
                      port="${spring.session.data.gemfire.port:${application.gemfire.client-server.port}}"/>


        <bean class="org.springframework.session.data.gemfire.config.annotation.web.http.GemFireHttpSessionConfiguration"
                  p:maxInactiveIntervalInSeconds="30"/>
```

首先，我们使用&lt;context：annotation-config&gt;元素启用Spring注释配置，以便在Spring配置中声明的任何使用Spring支持的Spring或Standard Java注释的Spring bean都将被正确配置。

注册了一个PropertySourcesPlaceholderConfigurer，以便在我们的Spring XML配置元数据中替换META-INF / spring / application.properties文件中的属性值中的占位符。

接下来，我们使用GemFire系统属性配置GemFire服务器非常像我们的P2P示例。将mcast-port设置为0并且没有指定locator属性，我们的服务器将是独立的。我们还允许一个JMX客户端（例如Gfsh）使用特定于Ge​​mFire的JMX系统属性连接到我们的服务器。

然后我们创建一个使用我们的GemFire系统属性初始化的GemFire对等缓存的实例。

我们还设置了运行在localhost上的GemFire CacheServer实例，侦听端口11235，准备接受我们的客户端连接。

最后，我们通过注册GemFireHttpSessionConfiguration的实例，在客户端上使用相同的Spring Session功能，但我们将会话到期超时设置为30秒。我们稍后会解释这是什么意思。

GemFire Server配置可以通过以下方式进行引导：

```
@Configuration 
@ImportResource("META-INF/spring/session-server.xml") 
public class Application {

        public static void main(final String[] args) {
                new AnnotationConfigApplicationContext(Application.class)
                        .registerShutdownHook();
        }
}
```



