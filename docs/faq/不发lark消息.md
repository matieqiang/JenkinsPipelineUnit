---
date:       2024/9/2
author:     matieqiang
---

不发lark消息
===
<h2> 1. 问题描述 </h2>

不发lark消息

<h2> 2. 原因分析 </h2>

不发送lark消息似乎是受 "restrict project naming"配置影响。
测试结果是当 选择standard时不发送lark通知，具体原因可能还要看lark插件的源码，pattern可以发送通知。


<h2> 3. 解决方法 </h2>
- restrict project naming 的作用是限制jenkins job命名字符串的，允许3个值： standard pattern roleBased。
- controller 位置:  manage jenkins > system > restrict project naming
- jenkins helm chart 配置：jcasc-config.yaml

```
data:
  jcasc-default-config.yaml: |-
    jenkins
      projectNamingStrategy:
        pattern:
          namePattern: "^[a-zA-Z][a-zA-Z0-9_-]{2,49}"
          forceExistingJobs: true
```

