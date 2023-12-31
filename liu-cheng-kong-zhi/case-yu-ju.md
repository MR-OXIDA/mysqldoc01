# CASE语句

MySQL的CASE语句用于在查询中进行条件判断和结果返回。它类似于编程语言中的switch语句。

CASE语句有两种形式：简单CASE表达式和搜索CASE表达式。

1. 简单CASE表达式：

```
CASE expression
    WHEN value1 THEN result1
    WHEN value2 THEN result2
    ...
    ELSE result
END
```

在简单CASE表达式中，expression是要进行条件判断的表达式，value1、value2等是可能的取值，result1、result2等是对应取值的返回结果。如果expression的值与某个value相等，则返回对应的result。如果没有任何匹配的值，则返回ELSE后面的result。

示例：

```
SELECT column1, column2,
    CASE column3
        WHEN 'value1' THEN 'result1'
        WHEN 'value2' THEN 'result2'
        ELSE 'result'
    END AS result_column
FROM table;
```

2. 搜索CASE表达式：

```
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ...
    ELSE result
END
```

在搜索CASE表达式中，condition1、condition2等是条件表达式，result1、result2等是对应条件为真时的返回结果。如果某个条件为真，则返回对应的result。如果没有任何条件为真，则返回ELSE后面的result。

示例：

```
SELECT column1, column2,
    CASE
        WHEN column3 = 'value1' THEN 'result1'
        WHEN column3 = 'value2' THEN 'result2'
        ELSE 'result'
    END AS result_column
FROM table;
```

CASE语句可以嵌套使用以实现更复杂的条件逻辑，并且可以在SELECT、UPDATE、DELETE等不同的MySQL语句中使用。
