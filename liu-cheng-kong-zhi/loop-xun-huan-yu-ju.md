# LOOP循环语句

很抱歉，我之前给出的回答有误。MySQL确实有一种循环语句，即LOOP循环语句。LOOP语句用于重复执行一段代码块，直到满足特定的退出条件。

以下是LOOP语句的基本语法：

```sql
[begin_label:] LOOP
    statements;
    [IF condition THEN]
        LEAVE [begin_label];
    [END IF;]
END LOOP [end_label];
```

其中，`begin_label`和`end_label`是可选的标签，用于标识循环的起始和结束。

以下是一个简单的示例，演示如何使用LOOP语句在MySQL中进行循环：

```sql
DELIMITER //

CREATE PROCEDURE loop_example()
BEGIN
    DECLARE counter INT DEFAULT 1;
    
    my_loop: LOOP
        IF counter > 10 THEN
            LEAVE my_loop;
        END IF;
        
        -- 在这里编写您想要执行的代码
        -- 可以使用 counter 变量来进行计算或其他操作
        
        SET counter = counter + 1;
    END LOOP my_loop;
END //

DELIMITER ;

CALL loop_example();
```

上述示例创建了一个存储过程 `loop_example()`，其中使用了LOOP语句来重复执行一段代码块，直到 `counter` 变量的值大于10时退出循环。

请根据您的具体需求，修改和扩展上述示例代码来满足您的要求。
