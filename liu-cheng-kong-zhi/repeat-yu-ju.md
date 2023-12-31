# REPEAT语句

在MySQL中，REPEAT语句用于创建一个重复执行的循环，直到指定的条件不再满足为止。它是MySQL提供的另一种循环控制语句。

下面是REPEAT语句的基本语法：

```
REPEAT
    -- 循环体
    statements;
UNTIL condition
END REPEAT;
```

在REPEAT语句中，循环体中的语句会一直执行，直到满足UNTIL后面的条件为止。只有当条件不再满足时，循环才会结束。

下面是一个使用REPEAT语句的示例：

```sql
DECLARE counter INT DEFAULT 0;

REPEAT
    SET counter = counter + 1;
    
    -- 在这里执行其他操作
    SELECT counter;
    
UNTIL counter >= 10
END REPEAT;
```

在上面的示例中，循环体中的语句会一直执行，直到counter的值大于等于10为止。每次循环，counter的值都会增加，并通过SELECT语句进行输出。

希望这可以帮助到您！如果您有任何其他问题，请随时提问。
