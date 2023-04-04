### 메모리 사용률 강제 부하
```
log.info("over cpu usage");

int count = Runtime.getRuntime().availableProcessors();

for (int i = 0; i < count; i++) {

    log.info("processors count: " + count);
    new Thread(new Runnable() {

        long start = System.currentTimeMillis();
        long end = start + 30 * 1000;
        public void run() {
            while (System.currentTimeMillis() < end){}
        }
    }).start();
}
```