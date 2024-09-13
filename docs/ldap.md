---
date:       2024/5/30
author:     matieqiang
---

ldap
===

1. 开启 匿名用户所有权限，避免配置错误导致无法登录
   Dashboard > Manage Jenkins > Security > authorization > Authorization > anyone can do anything

2. install ldap plugin
3. 配置ldap Dashboard > Manage Jenkins > Security > authorization > Security Realm > LDAP
   - Server: ldap://ldap.anysso.com
   - Root DN: dc=anysso,dc=com
   - User search base: ou=people
   - User search filter: (uid={0})
   - Group search base: ou=groups
   - Group search filter: (member={0})
   - Manager DN: cn=admin,dc=anysso,dc=com
   - Manager Password: changeMe123456
   - Display Name LDAP attribute: cn
   - Email Address LDAP attribute: mail
   - Enable TLS: false
   - Disable Ldap Email Resolver: false
   - Enable cache: false
   - Group membership: false
   - Inhibit Insecure Deserialization: false
   - Disable Role Prefixing 
域名: ldap.anysso.com

## 配置认证策略 authorizationStrategy
```yaml
controller:
   JCasC:
      authorizationStrategy: |-
         roleBased:
           roles:
             global:
               - name: "admin"
                 description: "Jenkins administrators"
                 permissions:
                   - "Overall/Administer"
                 entries:
                   - user: "admin"
                   - user: "tieqiang.ma"
               - name: "readonly"
                 description: "Read-only users"
                 permissions:
                   - "Overall/Read"
                   - "Job/Read"
                 entries:
                   - user: "authenticated"
             items:
               - name: "pre"
                 description: "pre-staging job"
                 pattern: "pre.*"
                 permissions:
                   - "Job/Cancel"
                   - "Job/Build"
                   - "Job/Discover"
                   - "Job/Read"
                   - "Job/Workspace"
                   - "View/Read"
                 entries:
                   - user: "authenticated"
               - name: "prod"
                 description: "product job"
                 pattern: "Product.*"
                 permissions:
                   - "Job/Cancel"
                   - "Job/Build"
                   - "Job/Discover"
                   - "Job/Read"
                   - "Job/Workspace"
                   - "View/Read"
                 entries:
                   - user: "nan.wang"
                   - user: "qiang.liu"
                   - user: "wei.han"
                   - user: "jingtong.hua"
                   - user: "liwei.shang"
                   - user: "zhe.chen"
```



## 参考文档
- jcasc plugin : https://plugins.jenkins.io/configuration-as-code/
- https://stackoverflow.com/questions/77970650/jenkins-casc-role-strategy-cant-get-permissions-working-correctly
- https://github.com/jenkinsci/configuration-as-code-plugin/tree/master/demos/ldap
- https://github.com/jenkinsci/configuration-as-code-plugin/tree/master/demos/role-strategy-auth
