##### 服务端配置

我们只涵盖了方程的一边。 我们还需要一个GemFire服务器，我们的客户端可以将会话状态与服务器进行通话和发送以进行管理。



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



