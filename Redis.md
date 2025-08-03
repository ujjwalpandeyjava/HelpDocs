# Redis

Redis is a fast, in-memory key-value store used for caching, real-time data, and pub-sub messaging.

## Steps

- Add dependency

```XML
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-redis</artifactId>
</dependency>
```

- Add in application.properties
```
spring.redis.host=localhost
spring.redis.port=6379
spring.redis.password=yourpassword   # optional
spring.redis.timeout=2000ms          # optional
```

- Add on main
 
@EnableCaching

- Add Beans

```java beans
@Configuration
public class CacheConfig {
	@Bean
	public RedisTemplate<String, Object> redisTemplate(RedisConnectionFactory connectionFactory) {
	RedisTemplate<String, Object> template = new RedisTemplate<>();
	template.setConnectionFactory(connectionFactory);
	template.setKeySerializer(new StringRedisSerializer());
	template.setValueSerializer(new GenericJackson2JsonRedisSerializer());
	return template;
	}

  @Bean
  public RedisCacheManager cacheManager(RedisConnectionFactory redisConnectionFactory) {
    RedisCacheConfiguration cacheConfig = RedisCacheConfiguration.defaultCacheConfig()
      .entryTtl(Duration.ofMinutes(10))
      .serializeKeysWith(RedisSerializationContext.SerializationPair.fromSerializer(new StringRedisSerializer()))
      .serializeValuesWith(RedisSerializationContext.SerializationPair.fromSerializer(new GenericJackson2JsonRedisSerializer()));
    return RedisCacheManager.builder(redisConnectionFactory)
      .cacheDefaults(cacheConfig)
      .build();
  }
}
```

- Use case

```Java
@Cacheable(value = "items", key="#id", unless="#result == null", cacheManager = "cacheManager")
public Item getItemById(Long id) {
  // Expensive database call
}
```

## Windows

Redis is not officially supported on Windows. Can install Redis for development only.

[How to work with Redis on Windows](https://redis.io/docs/latest/operate/oss_and_stack/install/archive/install-redis/install-redis-on-windows/)

WSL2 to act like Linux.

## Mac

Start Redis on background

brew services start redis


## Run Redis on another Docker as central Cache system

Yes, recommended practice in modern development, as multiple applications can connect to the same Redis instance.

### How It Works

1. Run Redis in its own Docker container using the official Redis image.
2. Expose Redis port (default 6379) so other containers or apps can connect.
	- Start Redis Container `docker run -d --name redis -p 6379:6379 -v ~/redis_data:/data redis:latest` runs Redis in Persisting Data, and detached mode, names the container redis
3. Other applications (whether running in Docker containers or on your host) connect to the Redis container using the container’s network address and port
	- Connect From Other Containers
	- If your app is in another Docker container, connect using the Redis container’s name or network alias.
	- You can use Docker Compose to define both services in the same network, or use the --link option for simple cases.

	Example with Docker Compose:

	```text
	services:
		redis:
			image: redis:latest
			ports:
			- "6379:6379"
		myapp:
			build: .
			environment:
				- REDIS_HOST=redis
				- REDIS_PORT=6379
			depends_on:
				- redis
	```

	Now the app connects to redis:6379

	- Connect From Host or External Apps
	Use localhost:6379 if connecting from your host machine
