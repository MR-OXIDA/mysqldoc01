# 光标

在MySQL中，光标（Cursor）是一种用于遍历结果集的数据库对象。它可以被用于存储查询结果，并通过移动指针来逐行访问这些结果。

以下是一个使用光标的简单案例：

1. 创建一个表格：

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    salary DECIMAL(10, 2)
);
```

2. 插入一些数据：

```sql
INSERT INTO employees (id, name, age, salary) VALUES
(1, 'John Doe', 30, 5000.00),
(2, 'Jane Smith', 35, 6000.00),
(3, 'Mike Johnson', 40, 7000.00),
(4, 'Sarah Williams', 25, 4500.00),
(5, 'David Brown', 28, 5500.00);
```

3. 声明和打开光标：

```sql
DECLARE cur CURSOR FOR SELECT * FROM employees;
OPEN cur;
```

4. 使用循环来遍历结果集并输出每一行的数据：

```sql
DECLARE done INT DEFAULT FALSE;
DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;

read_loop: LOOP
    FETCH cur INTO emp_id, emp_name, emp_age, emp_salary;
    
    IF done THEN
        LEAVE read_loop;
    END IF;
    
    -- 在这里进行你想要的操作，比如输出员工信息
    SELECT CONCAT('ID:', emp_id, ', Name:', emp_name, ', Age:', emp_age, ', Salary:', emp_salary) AS employee_info;
END LOOP;

CLOSE cur;
```

上述示例中，我们首先创建一个名为"employees"的表格，并插入了一些数据。然后，我们声明并打开了一个光标，该光标用于选择所有员工的信息。

接下来，我们使用循环和FETCH语句从光标中获取每一行的数据，并通过IF条件判断是否已经遍历完结果集。在循环内部，你可以根据需要执行任何操作，这里我们简单地将每个员工的信息输出到控制台。

最后，我们关闭光标以释放资源。

请注意，以上仅是一个简单的示例，实际应用中可能会有更复杂的逻辑和需求。此外，在MySQL中，游标主要用于存储过程（Stored Procedure）或函数（Function）中的数据处理，而不是常规查询。

### DECLARE 关键字

DECLARE 是一个关键字，用于在MySQL中声明变量、游标和处理程序。

1.  声明变量：您可以使用 DECLARE 关键字来声明一个变量，并指定其名称、数据类型和初始值（可选）。例如：

    DECLARE variable\_name data\_type \[DEFAULT initial\_value];

    这样就创建了一个名为 variable\_name 的变量，其数据类型为 data\_type，如果提供了 initial\_value，则变量将被初始化为该值。
2.  声明游标：您可以使用 DECLARE 关键字来声明一个游标，并指定其名称、SELECT语句以及其他属性。例如：

    DECLARE cursor\_name CURSOR FOR select\_statement;

    这样就创建了一个名为 cursor\_name 的游标，它将执行 select\_statement 查询语句并返回结果集。
3.  声明处理程序：您可以使用 DECLARE 关键字来声明一个处理程序，并指定要捕获的条件以及要执行的操作。例如：

    DECLARE CONTINUE HANDLER FOR condition\_value statement;

    这样就创建了一个处理程序，当出现满足 condition\_value 条件时，将执行 statement 语句。

请注意，在使用 DECLARE 关键字声明变量、游标或处理程序之前，必须先打开一个存储过程或函数块。这意味着 DECLARE 通常与 BEGIN 和 END 结构一起使用，以定义代码块的范围和作用域。
