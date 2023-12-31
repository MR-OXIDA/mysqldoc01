# HANDLER FOR语句

在MySQL中，DECLARE ... HANDLER FOR语句用于定义一个异常处理程序。它的语法如下：

DECLARE handler\_type HANDLER FOR condition\_value statement

其中，handler\_type可以是CONTINUE、EXIT或UNDO，用于指定异常处理程序的行为。condition\_value指定了需要处理的异常条件，可以是一个具体的异常类型，也可以是一个通配符。statement是在发生异常时要执行的语句。

以下是一些示例：

1. 定义一个异常处理程序，当发生MySQL错误1062（即唯一键冲突）时，打印错误信息并继续执行：

```sql
DECLARE CONTINUE HANDLER FOR 1062 BEGIN SELECT 'Duplicate key error!'; END;SQL
```

2. 定义一个异常处理程序，当发生MySQL错误1146（即表不存在）时，打印错误信息并退出：

```sql
DECLARE EXIT HANDLER FOR 1146 BEGIN SELECT 'Table does not exist!'; EXIT; END;
```

3. 定义一个异常处理程序，当发生任何错误时，回滚之前的操作：

```sql
DECLARE UNDO HANDLER FOR SQLEXCEPTION BEGIN ROLLBACK; END;
```

这些示例演示了如何使用DECLARE ... HANDLER FOR语句来定义不同类型的异常处理程序。根据需要，可以根据具体的异常条件和处理逻辑来定义自己的异常处理程序。
