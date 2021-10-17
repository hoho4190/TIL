# Building with JitPack

## Public Repository
- build.gradle.kts 추가
  ```kotlin
  // Gradle version: 7.2
  repositories {
    // ...
    maven("https://jitpack.io")
  }
  dependencies {
    // ...
  
    // 프로젝트의 모든 모듈
    implementation( "com.github.User:Repo:Version")
  
    // 프로젝트의 개별 모듈
  }
  ```

## Private Repository
- gradle.properties 추가
  ```properties
  # ...
  token=TOKEN1
  ```
- build.gradle.kts 추가
  ```kotlin
  repositories {
    // ...
    maven {
      url = uri("https://jitpack.io")
      credentials {
        val token: String by project
        // or
        // val token = project.property("token") as String
        username = token as String
      }
    }
  }
  ```

## Snapshots
스냅샷은 아직 출시되지 않은 버전입니다. 실제 버전과 스냅샷의 차이점은 스냅샷이 계속 업데이트될 수 있다는 것입니다.
스냅샷 버전은 개발 프로세스 중에 유용하며 JitPack은 두 가지 방법을 제공합니다.

- commit hash
  ```kotlin
  // commit hash
  implementation("com.github.jitpack:gradle-simple:COMMIT_HASH")
  ```

- branch-SNAPSHOT (replace ‘branch’ with any branch name, e.g. master)
  - `-SNAPSHOT`을 추가하면 마스터 브랜치에 최신 커밋이 빌드됩니다.
  ```kotlin
  // dependency on the latest commit in the master branch
  implementation("com.github.jitpack:gradle-simple:master-SNAPSHOT")
  ```

### SNAPSHOT 빌드를 캐시 관련
Gradle은 SNAPSHOT 빌드를 캐시할 수 있습니다. Gradle이 항상 빌드의 **최신** 버전을 선택하도록 설정이 필요합니다.

- build.gradle.kts 추가
  ```kotlin
  // 캐시하지 않음
  configurations.all {
    resolutionStrategy.cacheChangingModulesFor(0, TimeUnit.SECONDS)
  }
  ```
  - 새 스냅샷을 빌드하는 데 시간이 걸릴 수 있으므로 Gradle 시간 초과를 늘려야 할 수 있습니다.

- 터미널
  ```bash
  $ gradlew build --refresh-dependencies
  ```

## Reference
- [Jitpack Docs](https://jitpack.io/docs/)
- [Private Repositories](https://jitpack.io/docs/PRIVATE/)