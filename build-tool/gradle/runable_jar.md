plugins {
    id 'java'
}

group 'io.gana'
version '1.0-SNAPSHOT'

jar {
    manifest {
        attributes 'Main-Class': '[main class path]'
    }
    from {
        configurations.compileClasspath.collect {
            it.isDirectory() ? it : zipTree(it)
        }
    }
    duplicatesStrategy = DuplicatesStrategy.EXCLUDE
}

repositories {
    mavenCentral()
}

dependencies {
    implementation group: 'org.slf4j', name: 'slf4j-api', version: '1.7.32'
    implementation group: 'org.slf4j', name: 'slf4j-simple', version: '1.7.32'

    compileOnly 'org.projectlombok:lombok:1.18.24'
    annotationProcessor 'org.projectlombok:lombok:1.18.24'
    testAnnotationProcessor 'org.projectlombok:lombok:1.18.24'
    testImplementation 'org.projectlombok:lombok:1.18.24'

    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.8.1'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.8.1'
}

test {
    useJUnitPlatform()
}