---
description: 修改Neo4j的时区设置，让数据库时区和系统一致。
---

# 系统时区和数据库时区不一致

## 系统时区和数据库时区不一致

## 解决方法

停止数据库

在数据库配置文件  \conf\neo4j.conf 中添加

> \#\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
>
> \# Other Neo4j system properties
>
> \#\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
>
> dbms.db.timezone=SYSTEM
>
> \#dbms.logs.timezone has been replaced with dbms.db.timezone.
>
> \#dbms.logs.timezone=SYSTEM
>
> db.temporal.timezone=Asia/Shanghai

重启数据库，检查数据库时区  


![](.gitbook/assets/image%20%289%29.png)



