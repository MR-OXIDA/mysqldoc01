# CONDITION FOR语句

在MySQL中，DECLARE ... CONDITION FOR语句用于定义一个条件和与之关联的错误代码和错误消息。它的作用是在存储过程或函数中创建自定义的错误处理逻辑。

使用案例的例子如下：

```sql
DELIMITER //
CREATE PROCEDURE check_age(IN age INT)
BEGIN
    DECLARE age_error CONDITION FOR SQLSTATE '45000';
    DECLARE error_msg VARCHAR(255);
    
    IF age < 18 THEN
        SET error_msg = 'Age must be greater than or equal to 18.';
        SIGNAL age_error SET MESSAGE_TEXT = error_msg;
    END IF;
END //
DELIMITER ;
```

在上面的例子中，我们创建了一个存储过程check\_age，它接受一个age参数。我们定义了一个名为age\_error的条件，并将它与SQLSTATE '45000'（自定义错误代码）关联起来。然后，我们检查age是否小于18，如果是，则设置错误消息并使用SIGNAL语句引发age\_error条件。

这样，当我们调用存储过程check\_age并传递一个小于18的age值时，会引发age\_error条件，并返回自定义的错误消息"Age must be greater than or equal to 18."。
