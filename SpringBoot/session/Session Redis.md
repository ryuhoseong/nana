## redis 를 통한 session 관리
### 설정 (ebedded redis 대상)
    환경: Srping boot 2.7, Gradle 7.4
#### build.gradle
```
    implementation ('it.ozimov:embedded-redis:0.7.3') {
        exclude group: "org.slf4j", module: "slf4j-simple"
    }

    implementation 'org.springframework.session:spring-session-data-redis'

    implementation 'org.springframework.boot:spring-boot-starter-data-redis'
```

### properties
```
spring:  
  redis:
    host: localhost
    port: 6379
    password:
  session:
    store-type: redis
```

### java
```
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Profile;
import org.springframework.stereotype.Component;
import redis.embedded.RedisServer;

import javax.annotation.PostConstruct;
import javax.annotation.PreDestroy;

@Profile("local")
@Component
public class EmbeddedRedisServer {

    private final RedisServer redisServer;

    public EmbeddedRedisServer(@Value("${spring.redis.port}") int redisPort) {
        this.redisServer = RedisServer.builder()
                            .port(redisPort)
                            .setting("maxmemory 128M")
                            .build()
                            ;
    }

    @PostConstruct
    public void postConstruct() {
        redisServer.start();
    }

    @PreDestroy
    public void preDestroy() {
        redisServer.stop();
    }
}
```