### tar 배포 형태
```
project.archivesBaseName='wast-install'
project.version '0.2'


task tarTask(type: Tar) {
    into('/') {
        from 'build/libs'
        include '*.jar'
    }
    into('/') {
        from 'package'
    }

    destinationDirectory = file('build/distribution')
    extension 'tar'
    compression = Compression.GZIP
}
```