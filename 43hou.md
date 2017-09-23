##### 服务端配置

我们只涵盖了等式的一边。 我们还需要一个GemFire服务器端，我们的客户端可以与服务器进行通话并且将Session状态发送至服务器端，以进行管理。

在本示例中，GemFire服务端的Java配置如下：

```
@EnableGemFireHttpSession(maxInactiveIntervalInSeconds = 30) 1⃣️
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
}
```

1⃣️在服务器端也使用@EnableGemFireHttpSession注解来配置Spring Session。 这确保了客户端和服务端的区域名称匹配（在此示例中，我们使用默认的“ClusteredSpringSessions”）。 我们还将Session的过期时间设置为30秒。 稍后我们将看到如何使用这个过期时间。

2⃣️接下来，我们使用GemFire系统属性配置GemFire服务器，这非常像我们的P2P示例中的配置。 为了使服务端保持独立，我们将mcast-port设置为0并且没有指定locator属性。GemFire服务端还允许一个使用JMX客户端（例如Gfsh）来连接，但是该JMX必须的系统属性必须是特定于GemFire的。

3⃣️然后，我们创建一个基于GemFire系统属性的GemFire对等缓存实例。

4⃣️我们还设置了在localhost上运行的GemFire CacheServer实例，监听端口12480，准备接受我们的客户端连接。

5⃣️最后，我们将一个main方法声明为从命令行启动作为运行GemFire Server的入口点。

##### Java Servlet容器初始化 {#java-servlet-container-initialization-2}

我们的Spring Java配置创建了一个名为springSessionRepositoryFilter的Spring bean，该Bean实现了Filter接口。 springSessionRepositoryFilter bean负责使用基于GemFire支持的Spring Session来替换HttpSession。

为了使springSessionRepositoryFilter过滤器能够做到这一点，Spring需要加载我们的ClientConfig配置类。 还需要确保Servlet容器（即Tomcat）为每个请求使用springSessionRepositoryFilter。 幸运的是，Spring Session提供了一个名为AbstractHttpSessionApplicationInitializer的实用程序类，使这两个步骤都非常容易。

可以参考如下示例：

src/main/java/sample/Initializer.java

```
public class Initializer extends AbstractHttpSessionApplicationInitializer { 1⃣️

        public Initializer() {
                super(ClientConfig.class); 2⃣️
        }
}
```

> 注意：我们的类（Initializer）的名称并不重要。 重要的是需要扩展AbstractHttpSessionApplicationInitializer类即可。

1⃣️第一步是扩展AbstractHttpSessionApplicationInitializer类。 这确保了一个名为springSessionRepositoryFilter的Spring bean已经注册到我们的Servlet容器并应用于每个请求。

2⃣️AbstractHttpSessionApplicationInitializer还提供了一种便于Spring加载我们的ClientConfig的机制。

