# Maven学习笔记

## Maven简介

Maven是一个跨平台管理工具，是Apache组织的开源项目，主要服务于基于Java平台的项目构建、依赖管理和项目信息管理。
Maven可以帮助自动化构建过程，包括清理、编译、测试、报告生成、打包和部署等。Maven还可以帮助管理项目信息，包括项目描述、开发者列表、版本控制系统地址、许可证、缺陷管理系统地址等。

**构建**
构建是处理编写源代码外，需要进行的变异、单元测试、文档生成、打包和部署等繁琐而又必要的工作。

**其他构建工具**: *Make*, *Ant*(Another Neat Tool)等。

## POM

Maven项目的核心是pom.xml。POM(Project Object Model, 项目对象模型)定义了项目的基本信息，用于描述项目如何构建，声明项目依赖等。

POM中的groupId, artifactId, version三个元素定义了一个项目的基本坐标，在Maven世界中，任何的jar、pom或者war都可以基于这些基本坐标进行定位。

**groupID**定义了项目属于哪个组，组往往与项目所在的组织或公司关联，如org.gephi。

**artifactId**定义了当前项目在组中唯一的ID, 如gehpi-parent。

**version**指定了项目当前的版本，如0.9.3-SNAPSHOT。SNAPSHOT指快照，说明该项目还处于开发中，是不稳定的版本。

**name**则声明了一个对于用户更好的项目名称，不是必须的但推荐使用，如gephi。

通过使用POM，Maven能让项目对象模型最大程度地与实际代码相独立，即**解耦**或者**正交性**，避免了代码和POM文件相互影响。

## 使用Maven构建的项目

1. [Gephi - The Open Graph Viz Platform](https://github.com/gephi/gephi).
2. [SNAP - ESA's SentiNel Application Platform](https://github.com/senbox-org).

## 参考

1. 许晓斌. Maven实战. 北京：机械工业出版社, 2010. 

