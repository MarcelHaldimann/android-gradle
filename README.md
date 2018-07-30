# next405/android-gradle

## Included software

* OpenJDK 8
* Git
* Android SDK tools -> 27
* Gradle 4.9

## Example GitLab CI for [gradle-play-publisher](https://github.com/Triple-T/gradle-play-publisher)

```
image: next405/android-gradle
stages:
  - build

before_script:
  - mkdir /android/
  - echo $PLAYSTORE_API_KEY | base64 -d > /android/playstore-api-key.json

build:
  stage: build
  only:
    - branch
  script:
     - cd project/ch.organization.project/
     - gradle --stacktrace assembleRelease
     - gradle --stacktrace publishApkRelease
```