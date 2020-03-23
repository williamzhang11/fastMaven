# maven基础知识

maven是一个项目管理工具


## 1 提供的功能

### 1.1 依赖管理（jar包管理）
	
maven依赖管理指的是对项目中jar包的管理过程。最开始项目中一般把jar包放置在项目中。但是有了maven后，jar包是放置在仓库中，项目中只用配置仓库中jar包的坐标。

仓库的种类：本地仓库，远程仓库【私服】-一般是公司内部的，中央仓库（自动连的外网的仓库）。

仓库之间的关系：当我们启用一个maven工程时，maven工程会通过pom文件中的jar包坐标去本地仓库找对应jar包。
默认情况下，如果本地仓库没有对应jar包，maven工程会自动向中央仓库下载jar包， 如果有的话就可以启动了。
在公司中一般都会搭建自己的私服，可以配置先从私服下载，如果私服没有jar包，会从中央仓库下载，也可以从本地上传。

### 1.2 一键构建

maven自身集成了tomcat插件，可以对项目进行编译，测试，打包，安装，发布等操作。


maven clean :对之前的构建信息进行清理
maven compile:对src/main/java下目录进行编译
maven test:对src/main/java下目录进行编译
maven package:对本地项目进行打包，包是放在target下的
maven install:安装到本地仓库
maven deploy:打包上传到私服


### 1.3 pom文件(项目对象模型)

pom文件是对整个项目的描述，使用的xml格式。pom与java代码实现了解耦，当版本升级时，只需要修改pom

#### 1.4maven概念模型如下

![image](https://github.com/williamzhang11/fastMaven/blob/master/src/main/java/com/xiu/image/pom.png)

<project>节点中
xmlns是命名空间
xsi:schemaLocation是约束

#### 1.5坐标

坐标由GroupId，ArtifactId，Version组成，共同标识一个项目

GroupId:项目所在的组，一般是组织或公司
ArtifactId:项目名，当前项目在组中唯一的ID
Version:版本号,表示版本，SNAPSHOT表示快照，此项目还在开发中，不稳定。RELEASE:是正式版


实际开发中GroupId也可以对应到项目名称，而ArtifactId对应模块名称





















