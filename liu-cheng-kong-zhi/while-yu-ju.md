# WHILE 语句

MySQL的WHILE语句用于创建一个循环，只要指定的条件为真，就会执行循环体中的语句。下面是一个使用WHILE语句的简单示例：

```sql
DELIMITER //

CREATE PROCEDURE example_while()
BEGIN
    DECLARE i INT DEFAULT 1;
    
    WHILE i <= 10 DO
        -- 循环体中的语句
        SELECT i;
        SET i = i + 1;
    END WHILE;
END //

DELIMITER ;
```

在上面的示例中，我们创建了一个存储过程`example_while()`，它使用WHILE循环从1到10打印数字。在循环体中，我们首先使用`SELECT`语句打印当前的`i`值，然后使用`SET`语句将`i`增加1。

要执行上述存储过程，可以使用以下语句：

```sql
CALL example_while();
```

执行结果将是打印数字1到10。

请注意，WHILE循环的条件必须在循环体内部进行更新，否则可能导致无限循环。在上面的示例中，我们使用`SET`语句更新了`i`的值。
