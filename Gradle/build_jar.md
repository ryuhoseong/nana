### build jar ClassNotFoundException 현상
#### grade 7.0 미만
```
jar {
    manifest {
        attributes 'Main-Class': '[main class]'
    }
    from {
        configurations.compile.collect {
            it.isDirectory() ? it : zipTree(it)
        }
    }
}
```
#### grade 7.0 이상
```
jar {
    manifest {
        attributes 'Main-Class': '[main class]'
    }
    from {
        configurations.compileClasspath.collect {
            it.isDirectory() ? it : zipTree(it)
        }
    }
}
```