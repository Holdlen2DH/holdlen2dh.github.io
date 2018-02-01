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
* **groupId**, **artifactId**和**version**: 依赖的基本坐标，这是最重要的。
* **type**：依赖的类型，对应于项目坐标定义的packaging，一般不必声明。
* **scope**: 依赖范围。若依赖范围为test，则表示该依赖只对测试有效。
* **optional**: 标记依赖是否可选。
* **exclusions**: 用来排除传递性依赖。

**dependencies和dependency**: dependencies 元素下可以包含多个dependency元素以声明项目的依赖项。同样的，需要依赖的项目也通过groupId, artifactId和version三个基本坐标元素进行定位。




## 使用Maven构建的项目

1. [Gephi - The Open Graph Viz Platform](https://github.com/gephi/gephi).
2. [SNAP - ESA's SentiNel Application Platform](https://github.com/senbox-org).

## 参考

1. 许晓斌. Maven实战. 北京：机械工业出版社, 2010. 

