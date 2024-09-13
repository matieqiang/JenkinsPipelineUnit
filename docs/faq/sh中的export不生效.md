---
date:       2024/5/30
author:     matieqiang
---

sh中的export不生效
===
<h2> 1. 问题描述 </h2>

sh中的export不生效

**日志：**

```

```

<h2> 2. 原因分析 </h2>

在Jenkins Pipeline中，使用 sh 步骤执行 export 命令通常不会影响后续的 Shell 步骤，因为每个 sh 步骤在独立的 Shell 中运行。因此，变量的导出不会在后续步骤中生效。



<h2> 3. 解决方法 </h2>

直接指定命令全路径，如：

```bash
/var/jenkins-qa-agent/maven/mvn392/bin/mvn test -DsuiteXmlFile=/home/jenkins/agent/workspace/pre-staging-api-test/CommonTest/TestNg-suite-jenkins/bpsdata/data/IDEmailDetection/id/release-version.xml

```