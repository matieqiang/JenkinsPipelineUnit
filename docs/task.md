task
===
1. jenkins 接入ldap
2. 配置jenkins job
3. 优化测试执行：
   - 使用浅克隆的方式减少对git 历史版本的下载，提高下载速度，节省27分钟
   - 直接使用maven test ,不执行 clean操作 加快构建速度，节省10分钟
   - 多个任务共享maven 避免每个任务重复下载java依赖
   - git config --global http.postBuffer 1024000000
4. 配置testng suite
5. 梳理完目前所有产品
   1. 创建任务 country-current, country-history all-country-history


## 使用说明文档
- jenkins 任务介绍
  - 测试范围介绍
    - 产品维度
    - 当前版本
    - 历史版本
- 环境介绍
  - 支持pre-staging环境
  - gpu问题
  - 
- 维护
  - 研发:写接口文档
  - 测试:维护用例、测试套件、jenkins-job
- 目前还有什么问题
  - 因为有些测试用例只能支持北京环境，staging环境
