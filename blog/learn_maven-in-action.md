# Maven学习笔记

## Maven简介

[Maven](http://maven.apache.org/)是一个跨平台管理工具，是Apache组织的开源项目，主要服务于基于Java平台的项目构建、依赖管理和项目信息管理。
Maven可以帮助自动化构建过程，包括清理、编译、测试、报告生成、打包和部署等。Maven还可以帮助管理项目信息，包括项目描述、开发者列表、版本控制系统地址、许可证、缺陷管理系统地址等。

**构建**
构建是处理编写源代码外，需要进行的变异、单元测试、文档生成、打包和部署等繁琐而又必要的工作。

**其他构建工具**: *Make*, *Ant*(Another Neat Tool)等。

## POM

Maven项目的核心是pom.xml。POM(Project Object Model, 项目对象模型)定义了项目的基本信息，用于描述项目如何构建，声明项目依赖等。

POM中的groupId, artifactId, version三个元素定义了一个项目的基本坐标，在Maven世界中，任何的jar、pom或者war都可以基于这些基本坐标进行定位。

通过使用POM，Maven能让项目对象模型最大程度地与实际代码相独立，即**解耦**或者**正交性**，避免了代码和POM文件相互影响。

一个典型的单元测试包括三个步骤：(1) 准备测试类及数据；(2) 执行要测试的行为；(3) 检查结果。JUnit是Java中事实上的单元测试标准。JUnit 3和JUnit 4中，都约定所有需要执行测试的方法都以test开头。在JUnit 4中，需要执行测试的地方以@Test进行标注。

## Maven命令

**mvn clean compile**: 执行编译。

**mvn clean test**: 执行测试。

**mvn clean package**: 打包。项目编译和测试后，下一步需要打包(package)。POM中默认打包类型为jar。

执行test之前会先执行compile，执行package之前会先执行test，类似的，install之前会执行package。

## 坐标和依赖

### 坐标

Maven世界中拥有大量的jar、war等构件。引入坐标构件是为了唯一标识所有的这些构件。Maven坐标为各种构件引入了

**groupId**: 定义了项目属于哪个组，当前Maven项目隶属的实际项目，组往往与项目所在的组织或公司关联，如org.gephi。Maven项目和实际项目不一定是一对一的关系,一个实际项目往往被划分成很多个模块。 groupId不应该对应项目隶属的组织或公司，因为一个组织下会有很多实际的项目。groupId的表示方式与java包名的表示方式类似，通常与域名反向对应。

**artifactId**: 定义了当前项目在组中唯一的ID, 如gehpi-parent，定义了实际项目中的一个Maven项目(模块)。推荐做法是使用实际项目名称作为artifactId的前缀，以方便寻找实际构件。

**version**: 指定了项目当前的版本，如0.9.3-SNAPSHOT。SNAPSHOT指快照，说明该项目还处于开发中，是不稳定的版本。

**name**: 则声明了一个对于用户更好的项目名称，不是必须的但推荐使用，如gephi。

**packaging**: 定义了Maven项目的打包方式，打包方式通常与所生成构件的文件扩展名对应。在不定义packaging时，Maven会使用默认jar。

**classifier**: 帮助定义构件输出的一些附属构件，附属构件与主构件对应，使附属构件也拥有唯一的坐标。注意，不能直接定义项目的classifier，因为附属构件不是项目直接默认生成的，而是附加插件帮助生成的。

### 依赖

根元素project系的dependencies可以包含一个或多个dependency元素，以声明一个或多个项目依赖。每个项目依赖包含的元素有：

**dependencies和dependency**: dependencies 元素下可以包含多个dependency元素以声明项目的依赖项。同样的，需要依赖的项目也通过groupId, artifactId和version三个基本坐标元素进行定位。

* **groupId**, **artifactId**和**version**: 依赖的基本坐标，这是最重要的。
* **type**：依赖的类型，对应于项目坐标定义的packaging，一般不必声明。
* **scope**: 依赖范围。若依赖范围为test，则表示该依赖只对测试有效。
* **optional**: 标记依赖是否可选。
* **exclusions**: 用来排除传递性依赖。

#### 依赖范围

依赖范围就是用来控制依赖与三种classpath(编译classpath、测试classpath、运行classpath)的关系，Maven有以下几种依赖范围：

* **compile**: 编译依赖范围，若没有指定，则默认使用该依赖范围。
* **test**: 测试依赖范围。只对测试classpath有效，在编译主代码或者运行项目的使用时无法使用此类依赖。
* **provided**: 已提供依赖范围。使用此依赖范围的Maven依赖，对于编译和测试classpath有效，但是运行时无效。
* **runtime**: 运行时依赖范围。使用此依赖范围的Maven依赖，对于测试和运行classpath有效，但编译主代码时无效。
* **system**： 系统依赖范围。该依赖与三种classpath的关系，和provided依赖范围完全一致。使用system范围的依赖时必须通过systemPath元素显示地指定依赖文件的路径。但此依赖不是通过Maven仓库解析的，而且往往与本机系统确定的，可能造成构建的不可移植，影谨慎使用。
* **import**：导入依赖范围。该依赖范围不会对三种classpath产生实际的影响。

## 仓库

坐标和依赖是任何一个构件在Maven世界中的逻辑表示方式；而构建的物理表示方式是文件，Maven通过仓库来统一管理这些文件。

Maven世界中，任何一个依赖、插件或者项目构建的输出，都可以称为构件。任何一个构件都有一组坐标唯一标识。根据这个坐标可以定位其在仓库中的唯一存储路径，亦即Maven的仓库布局方式。

Maven分为两类：本地仓库和远程仓库。Maven根据坐标寻找构件的时候，首先会产看本地仓库，有则直接使用；没有或者需要查看是否有更新的构件版本，Maven会去远程仓库查找，发现后下载到本地仓库使用。如果本地仓库和远程仓库都没有需要的构件，Maven会报错。

**中央仓库**：Maven核心自带的远程仓库，包含了绝大部分开源的构件。本地没有所需构件时，Maven会尝试从中央仓库下载。

除了中央仓库和私服，还有很多其他公开的远程仓库，常见的有java.net, JBoss等。

**本地仓库**：默认情况下，不管是在Windows还是Linux上，每个用户在自己的用户目录下都有一个路径名为.m2/repository的仓库目录。 

有时候，由于某些原因，用户会想要自定义本地仓库目录地址，可以编辑~/.m2/settings.xml，设置localReposity元素的值为想要的仓库地址。需要注意的是，默认情况下，.m2/settings.xml文件是不存在的，需要从Maven安装目录复制过去在进行编辑

## 聚合和继承

软件设计人员往往会采用各种方式对软件划分模块，以得到更清晰的设计及更高的重用性。Maven的聚合特性能够把项目的各个模块聚合在一起构建，而Maven的继承特性则能帮助抽取各模块相同的依赖和插件等配置，在简化POM的同时，还能促进各个模块配置的一致性。

## 私服

私服不是Maven的核心概念,仅仅是一种衍生出来的特殊的Maven仓库。通过建立z自己的私服，可以降低中央仓库符合，节省外网带宽,加速Maven构建等。

三个专门的Maven仓库管理软件可以用来建立私服：Apache基金会的Archiva，JFrog的Artifactory和Sonatype的Nexus。




## 使用Maven构建的项目

1. [Gephi - The Open Graph Viz Platform](https://github.com/gephi/gephi).
2. [SNAP - ESA's SentiNel Application Platform](https://github.com/senbox-org).

## 参考

1. [Maven Getting Started Guide](http://maven.apache.org/guides/getting-started/index.html).
2. 许晓斌. Maven实战. 北京：机械工业出版社, 2010. 

