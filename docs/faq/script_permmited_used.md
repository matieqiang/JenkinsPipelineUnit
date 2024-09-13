---
date:       2024/5/27
author:     matieqiang
---

script_permmited_used
===
<h2> 1. 问题描述 </h2>
jenkins declarative pipeline中使用new File()时报错
```groovy
def dir = new File(path)
```

**日志：**

```
org.jenkinsci.plugins.scriptsecurity.sandbox.RejectedAccessException: Scripts not permitted to use new java.io.File java.lang.String
```

<h2> 2. 原因分析 </h2>
<h2> 3. 解决方法 </h2>

I had similar issue and I resolved it doing the following

Navigate to jenkins > Manage jenkins > In-process Script Approval
There was a pending command, which I had to approve.

see: https://stackoverflow.com/questions/38276341/jenkins-ci-pipeline-scripts-not-permitted-to-use-method-groovy-lang-groovyobject