# Publishing Gradle Android Library


Turn Android to be sdk gradle library


Modularize. 製作 lib: Publishing Gradle Android Library
* [使用Gradle发布项目到JCenter仓库](http://zhengxiaopeng.com/2015/02/02/%E4%BD%BF%E7%94%A8Gradle%E5%8F%91%E5%B8%83%E9%A1%B9%E7%9B%AE%E5%88%B0JCenter%E4%BB%93%E5%BA%93/)
* [Android拓展系列(12)--使用Gradle发布aar项目到JCenter仓库](http://www.cnblogs.com/qianxudetianxia/p/4322331.html)


## jCenter

[avast/android-styled-dialogs](https://github.com/avast/android-styled-dialogs)

### How to include

    dependencies {
        compile 'com.avast:android-styled-dialogs:2.2.0'
    }


* [Jcenter v.s. mavencentral()](http://stackoverflow.com/questions/24852219/android-buildscript-repositories-jcenter-vs-mavencentral)
    - JCenter is a Java repository in Bintray, which is the largest repo in the world for Java and Android OSS libraries, packages and components.
    - `jcenter()` is a superset of `mavenCentral()`, that encompasses many additional repositories and artifacts. 也就是說，**Bintray 包含 Maven Central**。
