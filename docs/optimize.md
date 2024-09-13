任务执行效率优化
===
## 1. maven clean 清理target过程需要很多时间
为了避免 clean 带来的额外的时间开销，去掉clean 命令，直接运行maven test 

```
代码中提到有这么几个情况，会认为jar包不是最新的：
1. jar包不存在（其实就是mvn clean的效果）
2. 传入比较的文件资源不存在
3. Resource with unknown modification date found，资源的修改时间未知
4. Resource with newer modification date found，jar包的最后修改时间比资源的最后修改时间早

总结
1. 理论上来讲不做mvn clean 得到的jar包应该是最新的，除非其他方式修改jar包中的内容而不修改源代码。
2. 平时可以用mvn install，而不进行chean节省时间（如果你觉得节省时间多的话），但最保险还是用 mvn clean install 生成最新的jar包或其他包
3. 不想用mvn clean又想保证jar包最新，建议添加 -Djar.forceCreation 参数

jar-plugin源代码地址：http://svn.apache.org/repos/asf/maven/plugins/tags/maven-jar-plugin-2.4
```
see: https://blog.csdn.net/jyg0723/article/details/52568023

## 2. git clone 时间太长
Git 仓库太大，导致 Clone 时间太久，超过 10 分钟。

使用Jenkins浅克隆，这个可以帮助你减少 Clone 所花费的时间，Shallow clone 是只获取当前仓库的最新版本，不会丢失代码更新

单个构建任务中：Source Code Management -> Git -> Additional Behaviours -> Shallow clone

Shallow clone:

Perform shallow clone, so that git will not download history of the project, saving time and disk space when you just want to access the latest version of a repository.



## 3. 优化maven构建时间
1. 使用 -T 参数，多线程构建
2. 使用 -DskipTests 参数，跳过测试
3. 使用 -Dmaven.test.skip=true 参数，跳过测试
4. 使用 -Dmaven.javadoc.skip=true 参数，跳过生成javadoc
5. 使用 -Dmaven.source.skip=true 参数，跳过生成源码包
6. 使用 -Dmaven.compile.skip=true 参数，跳过编译
7. 使用 -Dmaven.install.skip=true 参数，跳过安装
8. 使用 -Dmaven.deploy.skip=true 参数，跳过部署
9. 使用 -Dmaven.site.skip=true 参数，跳过生成站点



