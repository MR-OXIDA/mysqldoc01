# 创建函数

MySQL创建函数的语法如下：

```sql
DELIMITER //

CREATE FUNCTION function_name ([parameter1 datatype [, parameter2 datatype [, ...]]])
  RETURNS return_datatype
  [DETERMINISTIC]
  [COMMENT 'string']
  BEGIN
    -- 函数体代码
  END //

DELIMITER ;
```

其中，关键字和符号的含义如下：

* `DELIMITER`：用于指定分隔符，在函数定义中通常将其设置为`//`，在最后使用`DELIMITER ;`来恢复默认分隔符。
* `CREATE FUNCTION`：用于创建函数的语句。
* `function_name`：要创建的函数的名称。
* `parameter1, parameter2, ...`：可选参数列表，每个参数包括参数名和数据类型。
* `return_datatype`：函数返回值的数据类型。
* `DETERMINISTIC`：可选项，表示函数是否是确定性的（即对于给定的输入参数，始终返回相同的结果）。
* `COMMENT 'string'`：可选项，用于提供有关函数的注释。
* `BEGIN` 和 `END`：用于定义存储过程的主体代码块。

在函数体代码中，您可以使用各种 SQL 语句和逻辑控制结构来实现所需的功能。完成函数定义后，可以通过调用该函数来使用它。

{% hint style="danger" %}
请注意，创建函数需要具有适当的权限，并且函数名称应该是唯一的。
{% endhint %}

当您创建一个函数时，可以根据自己的需求编写函数体代码。以下是一个简单的例子来说明如何创建一个计算两个数之和的函数：

```sql
DELIMITER //

CREATE FUNCTION sum_numbers(a INT, b INT)
  RETURNS INT
  BEGIN
    DECLARE result INT;
    SET result = a + b;
    RETURN result;
  END //

DELIMITER ;
```

在这个例子中，我们创建了一个名为`sum_numbers`的函数，它接受两个整数参数`a`和`b`，并返回它们的和作为整数。

函数体代码部分使用了`DECLARE`语句来声明一个局部变量`result`，然后使用`SET`语句将`result`设置为`a + b`的结果。最后，通过`RETURN`语句返回计算得到的结果。

完成函数定义后，您可以像调用任何其他函数一样使用它。例如，可以执行以下查询来调用该函数并获取结果：

```sql
SELECT sum_numbers(5, 3);
```

这将返回结果`8`，即输入参数`5`和`3`的和。

请注意，上述示例仅演示了基本的函数创建和使用方法。实际情况下，函数可以更复杂，并且可以包含更多的逻辑和SQL语句以满足特定的需求。
