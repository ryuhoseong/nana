### log level 변경
```
curl --location 'http://127.0.0.1:8080/actuator/loggers/ROOT' \
--header 'Content-Type: application/json' \
--data '{
    "configuredLevel": "OFF",
    "effectiveLevel": "OFF"
}'
```