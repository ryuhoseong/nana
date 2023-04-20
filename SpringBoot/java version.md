## runtime java version 확인
```
String[] versionElements = System.getProperty("java.version").split("\\.");
int discard = Integer.parseInt(versionElements[0]);
int version;
if (discard == 1) {
    version = Integer.parseInt(versionElements[1]);
} else {
    version = discard;
}
```

### java9 이상
    String expectedVersion = "15";
    Runtime.Version runtimeVersion = Runtime.version();
    String version = String.valueOf(runtimeVersion.version().get(0));