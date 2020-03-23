# maven工程拆分与聚合

## 1.maven拆分思想
maven解决代码可重用问题是，通过把一个完整的项目，拆分成不同独立模块，这些独立模块都有各自独立坐标，在哪里需要其中的某个模块直接引用各自独立坐标即可。

一般模块划分为：dao,service,util,domain

## 2.maven聚合

把maven拆分的模块聚合到一起成为一个完整项目。

## 3.maven拆分步骤

### 3.1创建父工程

父工程中一般只有一个pom.xml
作用：管理公共jar包坐标

1.在idea中选择new->project(或者new->module)
2.选择maven
3.因为只需要一个pom.xml，因此archetype可以不用选择
4.填写要创建的仓库坐标，GroupId,ArtifactId,Version
5.注意此时如果项目位置project location需要改变的话，	在改变后的目录，需要手动创建父工程的目录。如改变后D:\javaprogram\fastMavenModule，需要添加D:\javaprogram\fastMavenModule\mavenparent
5.删除非必须的文件，如src


### 3.2创建dao子模块

1.右键父工程
2.选中Module
3.选择maven
4.与web没有交互可以不选择archetype
5.只需要填写ArtifactId。因为GroupId和Version已经在父工程中定义

查看dao子模块pom文件，会多了个parent,当前的dao子模块可以与parent共用groupId与version，但是得有自己的artifactId（项目名）。

查看父工程，多了个modules

### 3.3创建service子模块

参考3.2创建dao子模块

### 3.4创建web子模块

区别在于要使用archetype,选择org.apache.maven-archetype-webapp

因为使用了archetype，所以web中的pom中多了很多配置
如多了打包


## 工程与模块的区别

即创建时选择new->project与new->module的区别

工程与模块都不等于完整项目。

工程只能使用自己内部资源，没有父工程

模块是属于父工程的，模块一旦创建，所有父工程的资源都可以使用。子模块之间是没有关系的。如service中使用dao，就需要在service的pom中引入dao的坐标

父子工程是继承关系，已经建好了
平级之间的引用是依赖关系。依赖关系需要手动建立。








