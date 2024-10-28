### catalina log 파일 처리
```
implementation 'org.slf4j:slf4j-api'
implementation 'org.slf4j:slf4j-log4j12'

# Set root logger level to DEBUG and its only appender to A1.
log4j.rootLogger=${logging.level}, A1, FILE
# A1 is set to be a ConsoleAppender
log4j.appender.A1.Threshold=INFO
log4j.appender.A1=org.apache.log4j.ConsoleAppender
# A1 uses PatternLayout.
log4j.appender.A1.layout=org.apache.log4j.PatternLayout

# Define the file appender
log4j.appender.FILE.Threshold=${logging.level}
log4j.appender.FILE=org.apache.log4j.RollingFileAppender
log4j.appender.FILE.File=[로그 생성 경로]
log4j.appender.FILE.Append=true
log4j.appender.FILE.ImmediateFlush=true
log4j.appender.FILE.MaxFileSize=1MB
log4j.appender.FILE.MaxBackupIndex=10
log4j.appender.FILE.layout=org.apache.log4j.PatternLayout
log4j.appender.FILE.layout.ConversionPattern=[%d{yyyy-MM-dd HH:mm:ss} %-5p] %-25C{1} : %m%n
log4j.appender.FILE.encoding=UTF-8
```