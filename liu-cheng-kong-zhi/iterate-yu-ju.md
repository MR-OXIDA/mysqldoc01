# ITERATE语句

在MySQL中，ITERATE语句用于在循环中跳过当前迭代，并开始下一次迭代。它通常与循环控制语句（如WHILE或REPEAT）一起使用。

下面是ITERATE语句的基本语法：

```
ITERATE [label];
```

在循环中使用ITERATE时，它会跳过当前迭代，并开始下一次迭代。如果指定了一个标签（label），则ITERATE语句将跳转到该标签所在的位置。

下面是一个使用ITERATE语句的示例，结合WHILE循环：

```sql
DECLARE counter INT DEFAULT 0;

WHILE counter < 10 DO
    SET counter = counter + 1;
    
    IF counter = 5 THEN
        ITERATE;
    END IF;
    
    -- 在这里执行其他操作
    SELECT counter;
    
END WHILE;
```

在上面的示例中，当counter等于5时，ITERATE语句将跳过当前迭代，并开始下一次迭代。这样，当counter等于5时，SELECT语句不会执行。

