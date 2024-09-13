---
date: 2024/5/30
author: matieqiang
---

mvn test 运行testng.xml ，当所有用例都运行成功时不显示测试日志
===
<h2> 1. 问题描述 </h2>



**日志：**

```

```

<h2> 2. 原因分析 </h2>

    

```bash
    sh(
            script: '/var/jenkins-qa-agent/maven/mvn392/bin/mvn test -DsuiteXmlFile=' + suiteFullName,
            returnStdout: true
    )
```
<h2> 3. 解决方法 </h2>

    sh '/var/jenkins-qa-agent/maven/mvn392/bin/mvn test -DsuiteXmlFile=' + suiteFullName