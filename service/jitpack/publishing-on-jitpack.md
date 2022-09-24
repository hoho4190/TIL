# Publishing on JitPack

## Gradle projects(v 7.2)
### build.gradle.kts 설정
```kotlin
plugins {
    // ...

    // API 및 implementation 분리를 위한 플러그인
    `java-library`

    // Apache Maven 저장소에 빌드 아티팩트를 게시하는 기능을 제공
    `maven-publish`
}

groupId = "org.gradle.sample"
version = "0.0.1"

// Publications 설정
publishing {
    publications {
        create<MavenPublication>("maven") { // name ex) release
            artifactId = "my-library"
            from(components["java"])
        }
    }
}

dependencies {
    implementation(platform(kotlin("bom")))
    implementation(kotlin("stdlib-jdk8"))
    testImplementation("org.junit.jupiter:junit-jupiter-api:5.8.0")
    testRuntimeOnly("org.junit.jupiter:junit-jupiter-engine")
}

java {
    /**
     * Generating Sources JAR
     * 소스 코드(.java 파일)만 포함함. 디버깅에 사용
     */
    withSourcesJar()
    
    /**
     * Generating Javadoc JAR
     * Java 코드에서 API 문서를 HTML 형식으로 생성
     */
    withJavadocJar()
}

// 매니페스트 파일에 라이브러리 이름과 버전을 포함
tasks.jar {
    manifest {
        attributes(mapOf("Implementation-Title" to project.name,
            "Implementation-Version" to project.version))
    }
}
```

## Badges
```kotlin
[![Release](https://jitpack.io/v/User/Repo.svg)]
(https://jitpack.io/#User/Repo)
```
