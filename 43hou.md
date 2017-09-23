##### 服务端配置

我们只涵盖了等式的一边。 我们还需要一个GemFire服务器端，我们的客户端可以与服务器进行通话并且将Session状态发送至服务器端，以进行管理。

在本示例中，我们将使用以下GemFire Server Java配置：

```
@EnableGemFireHttpSession(maxInactiveIntervalInSeconds = 30) 
public class ServerConfig {

        static final int SERVER_PORT = 12480;

        static final String DEFAULT_GEMFIRE_LOG_LEVEL = "warning";
        static final String SERVER_HOST = "localhost";

        @SuppressWarnings("resource")
        public static void main(String[] args) throws IOException { 
                new AnnotationConfigApplicationContext(ServerConfig.class)
                        .registerShutdownHook();
        }

        @Bean
        static PropertySourcesPlaceholderConfigurer propertyPlaceholderConfigurer() {
                return new PropertySourcesPlaceholderConfigurer();
        }

        Properties gemfireProperties() { 
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
        CacheFactoryBean gemfireCache() { 
                CacheFactoryBean gemfireCache = new CacheFactoryBean();

                gemfireCache.setClose(true);
                gemfireCache.setProperties(gemfireProperties());

                return gemfireCache;
        }

        @Bean
        CacheServerFactoryBean gemfireCacheServer(Cache gemfireCache,
                        @Value("${spring.session.data.gemfire.port:" + SERVER_PORT + "}") int port) { 

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

在服务器上，我们也使用@EnableGemFireHttpSession注释来配置Spring Session。 这确保了客户端和服务器上的区域名称匹配（在此示例中，我们使用默认的“ClusteredSpringSessions”）。 我们还将会话超时设置为30秒。 稍后我们将看到如何使用这个超时。

接下来，我们使用GemFire系统属性配置GemFire服务器非常像我们的P2P示例。 将mcast-port设置为0并且没有指定locator属性，我们的服务器将是独立的。 我们还允许一个JMX客户端（例如Gfsh）使用特定于GemFire的JMX系统属性连接到我们的服务器。

然后，我们创建一个使用我们的GemFire系统属性初始化的GemFire对等缓存的实例。

我们还设置了在localhost上运行的GemFire CacheServer实例，侦听端口12480，准备接受我们的客户端连接。

最后，我们将一个主要方法声明为从命令行启动和运行GemFire Server的入口点。

##### Java Servlet容器初始化 {#java-servlet-container-initialization-2}



