### junit test시 spring log off 방법(banner 이전)
- test/resources/logback-test.xml 생생
```
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <include resource="org/springframework/boot/logging/logback/base.xml" />
    <logger name="org.springframework" level="OFF"/>
</configuration>
```