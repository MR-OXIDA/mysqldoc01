# 调用存储过程

要在MySQL中调用存储过程，可以使用CALL语句。下面是调用存储过程的基本语法：

```sql
CALL procedure_name(arguments);
```

其中，`procedure_name`是存储过程的名称，`arguments`是传递给存储过程的参数。如果存储过程没有参数，可以省略`arguments`部分。

以下是一个示例，演示如何调用名为`my_procedure`的存储过程：

```sql
CALL my_procedure();
```

如果存储过程有参数，可以在`arguments`部分传递参数值。例如，如果存储过程接受一个整数参数`param1`和一个字符串参数`param2`，可以这样调用：

```sql
CALL my_procedure(10, 'example');
```

请注意，存储过程必须在调用之前已经存在于数据库中。如果存储过程位于不同的数据库中，可以在调用时使用数据库限定符。例如，如果存储过程位于名为`my_database`的数据库中，可以这样调用：

```sql
CALL my_database.my_procedure();
```

这是在MySQL中调用存储过程的基本方法。根据具体的存储过程实现和需求，可能还需要处理存储过程的返回值或使用其他相关的MySQL语句和特性。



