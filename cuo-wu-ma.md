# 错误码

MySQL错误码是一个庞大的列表，包含了各种错误和异常情况的标识码。以下是一些常见的MySQL错误码和它们的含义：

* 1040：Too many connections（连接数过多）
* 1042：Can't get hostname for your address（无法获取你的地址的主机名）
* 1045：Access denied for user 'username'@'localhost'（用户名或密码错误）
* 1062：Duplicate entry 'value' for key 'key\_name'（唯一键冲突）
* 1146：Table 'table\_name' doesn't exist（表不存在）
* 1216：Cannot add or update a child row: a foreign key constraint fails（外键约束失败）
* 1451：Cannot delete or update a parent row: a foreign key constraint fails（外键约束失败）
* 1644：Unsupported statement in stored function or trigger（存储函数或触发器中不支持的语句）
* 2002：Can't connect to local MySQL server through socket 'socket\_name'（无法通过套接字连接到本地MySQL服务器）
* 2006：MySQL server has gone away（MySQL服务器断开连接）
* 2013：Lost connection to MySQL server during query（查询期间与MySQL服务器的连接丢失）
* 2059：Authentication plugin 'plugin\_name' reported error（认证插件报错）
* 1364：Field 'field\_name' doesn't have a default value（字段没有默认值）

这只是一小部分常见的MySQL错误码，实际上还有很多其他的错误码。如果你遇到了特定的错误码，可以在MySQL官方文档中找到完整的MySQL错误码列表。
