---
date:       2024/7/19
author:     matieqiang
---

configure-as-code
===

## 1. 介绍
jenkins 配置是复杂的，通过configure as code 配置jenkins,以纯文本、yaml语法管理jenkins配置，可以快速定义、恢复配置。

## 2. 参考
配置的字段名和webUI 显示的有写差别，所以需要一个参考文件，这个文件可以在 management jenkins > configure as code > documents找到, https://localhost/manage/configuration-as-code/reference
这里面包含了所有jenkins配置字段