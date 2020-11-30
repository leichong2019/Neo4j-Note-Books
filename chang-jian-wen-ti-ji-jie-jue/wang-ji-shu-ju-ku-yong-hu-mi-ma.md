---
description: 如果忘记了数据库用户密码，如何重置密码恢复登陆权限。
---

# 忘记数据库用户密码

## 问题描述

![&#x5728;&#x767B;&#x9646;&#x754C;&#x9762;&#x8F93;&#x5165;&#x7528;&#x6237;&#x540D;&#x5BC6;&#x7801;&#xFF0C;&#x9875;&#x9762;&#x4E0B;&#x63D0;&#x793A;&#x9A8C;&#x8BC1;&#x5931;&#x8D25;](../.gitbook/assets/image%20%281%29.png)

![&#x670D;&#x52A1;&#x5668;&#x7AEF;&#x663E;&#x793A;&#x9A8C;&#x8BC1;&#x5931;&#x8D25;](../.gitbook/assets/image%20%282%29.png)

## 解决方法

### 如果有其他可用的用户（community版本）

1. 用正常的用户登录neo4j数据库。
2. use system 运行切换至system数据库
3.  show users 查看目前系统中可用的用户及状态。

![show users &#x67E5;&#x770B;&#x76EE;&#x524D;&#x7CFB;&#x7EDF;&#x5404;&#x79CD;&#x53EF;&#x7528;&#x7ED9;&#x7684;&#x8D26;&#x6237;&#x5217;&#x8868;](../.gitbook/assets/image%20%283%29.png)

4.  通过Alter user xxx set password 'yyy'直接修改用户的登陆密

### 

```sql
alter user xxxx set password 'yyyyy' change not required
```

![Alter user xxx set password &apos;yyy&apos;&#x76F4;&#x63A5;&#x4FEE;&#x6539;&#x7528;&#x6237;&#x7684;&#x767B;&#x9646;&#x5BC6;&#x7801;](../.gitbook/assets/image%20%285%29.png)

### 如果没有可正常登陆的用户（community版本）

* 先关闭数据库
* 修改 \conf\neo4j.conf 配置文件  _dbms.security.auth\_enabled=false_，不启用账户密码验证

![dbms.security.auth\_enabled=false](../.gitbook/assets/image%20%286%29.png)

* 重新启动数据库
* 输入或省略用户名，省略密码，直接连接即可登录

![&#x4E0D;&#x9700;&#x8981;&#x5BC6;&#x7801;&#x76F4;&#x63A5;&#x767B;&#x5F55;](../.gitbook/assets/image%20%288%29.png)

* 登录之后，用上一步中的alter user语句修改重置用户密码。
* 关闭数据库
* 将 dbms.security.auth\_enabled=true 配置恢复，重启数据库即可以正常登陆了。

> 参考文档，链接
>
> [Neo4j管理文档](https://neo4j.com/docs/cypher-manual/4.2/administration/security/users-and-roles/#administration-security-users-show-current)

