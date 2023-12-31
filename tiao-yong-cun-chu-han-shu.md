# 调用存储函数

要在MySQL中调用存储函数，可以使用SELECT语句。下面是调用存储函数的基本语法：

```sql
SELECT function_name(arguments);
```

其中，`function_name`是存储函数的名称，`arguments`是传递给函数的参数。如果函数没有参数，可以省略`arguments`部分。

以下是一个示例，演示如何调用名为`my_function`的存储函数：

```sql
SELECT my_function();
```

如果函数有参数，可以在`arguments`部分传递参数值。例如，如果函数接受一个整数参数`param1`和一个字符串参数`param2`，可以这样调用：

```sql
SELECT my_function(10, 'example');
```

请注意，存储函数必须在调用之前已经存在于数据库中。如果函数位于不同的数据库中，可以在调用时使用数据库限定符。例如，如果函数位于名为`my_database`的数据库中，可以这样调用：

```sql
SELECT my_database.my_function();
```

这是在MySQL中调用存储函数的基本方法。根据具体的函数实现和需求，可能还需要处理函数的返回值或使用其他相关的MySQL语句和特性。
