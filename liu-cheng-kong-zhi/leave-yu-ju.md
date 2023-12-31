# LEAVE语句

在MySQL中，LEAVE语句用于在循环中提前退出循环。它通常与循环控制语句（如LOOP、WHILE、REPEAT）结合使用。

以下是LEAVE语句的基本语法：

```
LEAVE [label];
```

其中，`label`是可选的标签，用于指定要退出的循环。如果没有指定标签，则LEAVE语句将退出当前最内层的循环。

以下是一个示例，演示如何在MySQL中使用LEAVE语句：

```
CREATE PROCEDURE loop_example()
BEGIN
    DECLARE counter INT DEFAULT 1;
    
    my_loop: LOOP
        IF counter > 5 THEN
            LEAVE my_loop;
        END IF;
        
        -- 在这里编写您想要执行的代码
        
        SET counter = counter + 1;
    END LOOP my_loop;
    
    -- 在循环之后的代码
    -- ...
    
END;
```

上述示例中，使用了LOOP语句创建了一个循环，当 `counter` 变量的值大于5时，使用LEAVE语句提前退出循环。

请根据您的具体需求，将LEAVE语句与适当的循环控制语句结合使用，以实现您所需的循环行为。
