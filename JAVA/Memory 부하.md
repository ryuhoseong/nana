### 메모리 사용률 강제 부하

```
List<byte[]> list = new ArrayList<>();
int index = 1;

while (true) {
    // 1MB each loop, 1 x 1024 x 1024 = 1048576
    byte[] b = new byte[1048576];
    list.add(b);
    Runtime rt = Runtime.getRuntime();
    log.info(index++ + " free memory: " + rt.freeMemory());
}
```