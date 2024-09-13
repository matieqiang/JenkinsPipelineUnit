---
date:       2024/9/4
author:     matieqiang
---

gdsl文件
===
在 Jenkins Pipeline 中，GDSL 文件（Groovy DSL 文件）用于定义和描述 Jenkins Pipeline DSL 的结构、方法和属性，
从而增强 IDE（如 IntelliJ IDEA）对 Jenkins Pipeline 脚本的支持。
这包括代码补全、语法高亮、文档提示等功能，使得在编写 Jenkins Pipeline 脚本时更加高效和直观。

## 主要功能和作用
1. 代码补全:

提供 Pipeline DSL 方法、步骤和属性的代码补全。
减少拼写错误，提升编写速度和准确性。
2. 语法高亮:

提供语法高亮和结构化视图，使脚本更加易读和易于理解。
3. 文档提示:

在编写代码时提供方法和属性的文档提示，帮助开发者理解功能和用法。
4. 错误提示:

通过提供 IDE 对 Pipeline DSL 的更好理解，能够提前检测出常见的脚本错误。

## 如何使用
使用 GDSL 文件的步骤
创建 GDSL 文件:

创建一个扩展名为 .gdsl 的文件，例如 jenkins-pipeline.gdsl。
编写 GDSL 规则:

在 GDSL 文件中，使用 GDSL 语法定义 Jenkins Pipeline 的结构、方法和文档。
将 GDSL 文件添加到项目中:

将 GDSL 文件放置在项目的资源目录中，通常是 src/main/resources 或 src/main/groovy。