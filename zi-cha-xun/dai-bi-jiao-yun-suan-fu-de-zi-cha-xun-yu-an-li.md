# 带比较运算符的子查询与案例

当涉及到比较运算符时，子查询可以用于检索满足特定条件的数据。以下是两个示例，分别使用带有比较运算符的子查询：

1. 使用比较运算符的子查询示例（使用`>`运算符）： 假设我们有一个名为`products`的表，其中包含产品的信息，包括产品名称和价格。我们想要找到价格高于平均价格的产品。可以使用子查询来实现这一点。

```sql
SELECT product_name, price
FROM products
WHERE price > (SELECT AVG(price) FROM products);
```

在上面的示例中，子查询 `(SELECT AVG(price) FROM products)` 返回了产品价格的平均值。然后，主查询使用比较运算符 `>` 来筛选出价格高于平均价格的产品。

2. 使用比较运算符的子查询示例（使用`IN`运算符）： 假设我们有两个表，一个是`customers`表，包含客户的信息，另一个是`orders`表，包含订单的信息。我们想要找到已经下过订单的客户。可以使用子查询和`IN`运算符来实现这一点。

```sql
SELECT customer_name
FROM customers
WHERE customer_id IN (SELECT DISTINCT customer_id FROM orders);
```

在上面的示例中，子查询 `(SELECT DISTINCT customer_id FROM orders)` 返回了已经下过订单的客户的唯一标识符。主查询使用`IN`运算符来筛选出`customers`表中具有这些唯一标识符的客户。

这些是使用比较运算符的子查询的示例。您可以根据具体的需求和数据模型进行调整和修改。
