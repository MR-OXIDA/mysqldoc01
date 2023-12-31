# 带in的子查询与案例

带有 `IN` 的子查询也是一种常见的用法，用于在主查询中筛选出与子查询结果匹配的行。`IN` 子查询将主查询中的值与子查询返回的结果进行比较，并返回匹配的结果。

以下是一个示例，使用带有 `IN` 的子查询来查找所有订单已经发货的客户：

```sql
SELECT *
FROM customers
WHERE customer_id IN (
    SELECT customer_id
    FROM orders
    WHERE status = 'Shipped'
);
```

在上面的例子中，主查询选择了 `customers` 表中的所有行，但只返回那些在子查询中返回的订单客户 ID 匹配的客户。子查询选择了 `orders` 表中状态为 "Shipped" 的订单的客户 ID。

使用 `IN` 子查询时，子查询必须返回一个列，该列将与主查询中的值进行比较。在上面的例子中，子查询返回的是 `orders` 表中已发货订单的客户 ID。

`IN` 子查询可以根据具体的需求进行修改和扩展。您可以在子查询中添加其他条件，以进一步筛选结果。
