### major version
    javap -verbose ClassName | grep major

### jvm 정보
    -XX:NativeMemoryTracking=summary
    jcmd <pid> VM.native_memory summary

### oom dump
    -XX:+HeapDumpOnOutOfMemoryError
    -XX:HeapDumpPath=/var/log

### heap
    -Xms[] -Xmx