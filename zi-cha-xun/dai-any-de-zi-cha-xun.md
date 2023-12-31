# 带any的子查询

带有 `ANY` 的子查询是一种常见的子查询类型，它用于比较主查询中的某个值与子查询返回的多个值中的任意一个。

下面是一个使用 `ANY` 的子查询的示例：

假设有两个表：`orders` 和 `customers`。`orders` 表包含订单信息，其中的 `customer_id` 列表示订单所属的客户。`customers` 表包含客户信息，其中的 `customer_id` 列是主键。

现在我们想要找出所有至少有一个订单的客户。可以使用带有 `ANY` 的子查询来实现：

```sql
SELECT customer_id, customer_name
FROM customers
WHERE customer_id = ANY (SELECT customer_id FROM orders)
```

在上面的示例中，子查询 `(SELECT customer_id FROM orders)` 返回了所有存在订单的客户的 `customer_id`。主查询使用 `WHERE` 子句和 `ANY` 来判断主查询中的 `customer_id` 是否等于子查询返回的任意一个 `customer_id`。

这样，主查询将返回所有至少有一个订单的客户的 `customer_id` 和 `customer_name`。

希望以上示例能够帮助你理解带有 `ANY` 的子查询的用法。
