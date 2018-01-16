# 说明

该库主要用于发布到Maven私服提供便利。

# 使用方式

## 对Maven私服信息进行配置
在library的build.gradle文件中直接添加如下代码：

```groovy
apply from: 'https://github.com/foolchen/Android-MavenPush/blob/master/maven_push.gradle'
```

并且在工程根目录下添加`maven_push.properties`，用于存放Maven服务器相关信息。内容定义如下：
RELEASE_REPO_URL=Maven Release地址
SNAPSHOTS_REPO_URL=Maven Snapshots地址
NEXUS_USERNAME=Maven私服用户名
NEXUS_PASSWORD=Maven私服密码

**注意：**为了Maven私服信息的保密，请在`.gitignore`文件中添加对于`maven_push.properties`文件的忽略。

## 对库的信息进行配置

// 库的版本，如果添加了SNAPSHOT后缀，则会在上传时自动使用SNAPSHOTS_REPO_URL的值
VERSION_NAME=0.1.0-SNAPSHOT
// 库的分组id
POM_GROUP_ID=com.foolchen.lib
// 库的唯一id
POM_ARTIFACT_ID=maven_push
// 库的名称
POM_NAME=MavenPush
// 库的打包类型，此处如果为Android Library，则为aar；如果是Java Library，则应为jar
POM_PACKAGING=aar
// 库的描述
POM_DESCRIPTION=发布到Maven私服的说明
// 库的地址
POM_URL=https://github.com/foolchen/Android-MavenPush
// 开源协议信息
POM_LICENCE_NAME=Apache License Version 2.0
POM_LICENCE_URL=http://www.apache.org/licenses/LICENSE-2.0.txt
POM_LICENCE_DIST=Apache License Version 2.0
// 开发者信息
POM_DEVELOPER_ID=chenchong
POM_DEVELOPER_NAME=chenchong

# 打包Kotlin源码

打包时默认只会打包Java源码，如果需要打包Kotlin源码，则需要在library的build.gradle文件中添加如下代码：

```groovy
android{
    sourceSets {
    main {
      java {
        include '**/*.java'
        include '**/*.kt'
      }
    }
  }
}
```

