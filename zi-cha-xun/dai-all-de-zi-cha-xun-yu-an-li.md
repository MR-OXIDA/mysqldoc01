# 带all的子查询与案例

带有`ALL`的子查询在MySQL中的作用是比较一个值与子查询返回的多个值中的所有值。下面是一个示例，展示了如何使用带有`ALL`的子查询来查找所有订单都已经发货的客户：

假设我们有两个表，一个是`Customers`表，包含客户的信息，另一个是`Orders`表，包含订单的信息。我们想要找到所有订单都已经发货的客户。

```sql
SELECT *
FROM Customers
WHERE CustomerID = ALL (SELECT CustomerID FROM Orders WHERE Shipped = 1);
```

在上面的示例中，子查询`(SELECT CustomerID FROM Orders WHERE Shipped = 1)`返回了所有已经发货的订单的`CustomerID`。然后，我们使用`ALL`关键字将客户表中的`CustomerID`与子查询返回的值进行比较。只有当客户表中的`CustomerID`与子查询返回的所有值都匹配时，该客户才会被返回。

请注意，`ALL`关键字可以省略，因为它是默认的比较操作符，但为了清晰起见，我在示例中使用了它。
