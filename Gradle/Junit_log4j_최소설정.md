### builde.gradle 에 추가
```
testImplementation group: 'org.slf4j', name: 'slf4j-api', version: '1.7.32'
testImplementation group: 'org.slf4j', name: 'slf4j-simple', version: '1.7.32'

compileOnly 'org.projectlombok:lombok:1.18.24'
annotationProcessor 'org.projectlombok:lombok:1.18.24'
testAnnotationProcessor 'org.projectlombok:lombok:1.18.24'
testImplementation 'org.projectlombok:lombok:1.18.24'
  
testImplementation 'org.junit.jupiter:junit-jupiter-api:5.8.1'
testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.8.1'
```
### 참조
    import org.slf4j.Logger;  
    import org.slf4j.LoggerFactory;  
    Logger logger = LoggerFactory.getLogger([Class 명].class);