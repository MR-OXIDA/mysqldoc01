# union 合并查询结果集

`UNION` 是一种用于合并两个或多个查询结果集的操作。它将两个查询的结果组合成一个结果集，并自动去除重复的行。以下是一个使用 `UNION` 合并查询结果集的示例：

假设我们有两个表，一个是 `employees` 表，包含员工的信息，另一个是 `customers` 表，包含客户的信息。我们想要获取所有员工和客户的姓名，并将它们合并成一个结果集。

```sql
SELECT employee_name
FROM employees
UNION
SELECT customer_name
FROM customers;
```

在上面的示例中，第一个查询 `SELECT employee_name FROM employees` 返回了所有员工的姓名，第二个查询 `SELECT customer_name FROM customers` 返回了所有客户的姓名。通过使用 `UNION` 运算符，这两个查询的结果集被合并成一个结果集，并且重复的行会被自动去除。

需要注意的是，`UNION` 运算符要求两个查询的列数和数据类型必须相同或兼容。如果列数或数据类型不匹配，可以使用 `CAST` 函数来进行类型转换，以确保两个查询兼容。

另外，如果需要保留重复的行，可以使用 `UNION ALL` 运算符，它会将两个查询的结果集合并在一起，包括重复的行。

这是使用 `UNION` 运算符合并查询结果集的示例。您可以根据具体的需求和数据模型进行调整和修改。
