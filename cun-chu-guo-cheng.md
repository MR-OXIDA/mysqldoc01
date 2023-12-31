# 存储过程

MySQL存储过程的语法如下所示：

```sql
DELIMITER //

CREATE PROCEDURE procedure_name ([parameter_list])
    [characteristics]
BEGIN
    -- 存储过程体，包含一系列SQL语句和逻辑控制结构
END //

DELIMITER ;
```

让我们来详细解释一下这个语法：

* `DELIMITER`语句用于指定自定义分隔符，以便在创建存储过程时使用。默认情况下，分号(`;`)被用作语句的结束符，但是在存储过程中会有多条语句，因此需要一个不同的分隔符。
* `CREATE PROCEDURE`语句用于创建存储过程。你需要为存储过程提供一个名称，并可以选择性地添加参数列表。参数列表由括号内的参数组成，每个参数都包含参数名和数据类型。
* `characteristics`部分是可选的，它允许你指定存储过程的特性，例如`DETERMINISTIC`、`CONTAINS SQL`等。这些特性影响存储过程的执行方式和优化器的行为。
* `BEGIN`和`END`之间的代码块是存储过程的主体。你可以在这里编写一系列的SQL语句和逻辑控制结构（如条件判断、循环等）来实现所需的功能。

在存储过程的主体中，你可以使用各种SQL语句来查询、插入、更新或删除数据。你还可以使用流程控制结构（如IF语句、CASE语句、LOOP语句等）对数据进行逻辑操作。

最后，`DELIMITER ;`语句将分隔符恢复为默认值，以便在之后的SQL语句中使用分号作为结束符。

### 代码示例

下面是一个简单的例子：

```sql
CREATE PROCEDURE GetCustomer(IN customerId INT)
BEGIN
    SELECT * FROM customers WHERE id = customerId;
END;
```

这个例子创建了一个名为`GetCustomer`的存储过程，它接收一个整数类型的参数`customerId`，并从`customers`表中返回与该ID匹配的行。

要调用存储过程，你可以使用`CALL`语句，后跟存储过程的名称和相应的参数值。例如：

```sql
CALL GetCustomer(1);
```

这将调用`GetCustomer`存储过程，并传递参数值为1。

除了输入参数，存储过程还可以有输出参数和返回结果集。你可以在存储过程内部使用`OUT`关键字定义输出参数，并使用`SELECT`语句返回结果集。

### DETERMINISTIC和NOT DETERMINISTIC的区别以及作用

在MySQL存储过程中，DETERMINISTIC和NOT DETERMINISTIC是两个关键字，用于指定存储过程的确定性。

1. DETERMINISTIC（确定性）：当一个存储过程被标记为DETERMINISTIC时，它意味着对于给定的输入参数，存储过程的执行结果是确定的，即相同的输入参数将始终产生相同的输出结果。这意味着存储过程不会产生随机或不确定的结果。
2. NOT DETERMINISTIC（非确定性）：当一个存储过程被标记为NOT DETERMINISTIC时，它意味着对于给定的输入参数，存储过程的执行结果可能是不确定的，即相同的输入参数可能会产生不同的输出结果。这意味着存储过程可能会产生随机或不确定的结果。

这两个关键字的作用在于帮助MySQL优化器进行查询优化和缓存。当存储过程被标记为DETERMINISTIC时，MySQL可以在执行过程中对其进行优化，并且可以缓存相同输入参数的结果以提高性能。而当存储过程被标记为NOT DETERMINISTIC时，MySQL会在每次调用存储过程时都执行它，并且不会缓存结果。

需要注意的是，默认情况下，存储过程被认为是NOT DETERMINISTIC的，即使你没有显式地指定。因此，如果你确定你的存储过程是确定性的，可以使用DETERMINISTIC关键字来提高性能并启用结果缓存。

下面是一个示例，展示了如何在MySQL存储过程中使用DETERMINISTIC关键字：

```sql
CREATE PROCEDURE my_procedure(IN param INT)
DETERMINISTIC
BEGIN
    -- 存储过程的逻辑
END;
```

希望这个解释能够帮助你理解DETERMINISTIC和NOT DETERMINISTIC在MySQL存储过程中的区别和作用。

### NO SQL和CONTAINS SQL的区别以及作用

在MySQL存储过程中，NO SQL和CONTAINS SQL是两个关键字，用于定义存储过程的特性和行为。它们的区别和作用如下：

1. NO SQL：当一个存储过程被标记为NO SQL时，表示该存储过程不包含任何SQL语句。换句话说，它不会访问或修改数据库中的数据。这种类型的存储过程通常用于执行一些与数据库无关的计算或业务逻辑。NO SQL存储过程可以提高性能，因为它们不需要与数据库进行交互。
2. CONTAINS SQL：当一个存储过程被标记为CONTAINS SQL时，表示该存储过程包含SQL语句。这意味着它可能会访问或修改数据库中的数据。CONTAINS SQL存储过程通常用于执行与数据库相关的操作，例如查询数据、更新数据或插入数据等。

这两个关键字的作用是告诉MySQL存储过程编译器有关存储过程的信息，以便进行优化和执行计划的生成。通过使用这些关键字，MySQL可以更好地理解存储过程的行为，并做出相应的优化决策，以提高性能和执行效率。

需要注意的是，如果一个存储过程没有被明确标记为NO SQL或CONTAINS SQL，默认情况下它将被认为是CONTAINS SQL的。在编写存储过程时，根据实际需求选择适当的关键字来定义存储过程的特性。

### CREATE PROCEDURE语句可以包含以下参数配置

1. procedure\_name：存储过程的名称。
2. parameter\_list：存储过程的参数列表。参数可以是输入参数（IN）、输出参数（OUT）或者输入输出参数（INOUT）。
   * IN参数：存储过程中的输入参数，只能在存储过程内部使用。
   * OUT参数：存储过程中的输出参数，可以在存储过程内部赋值，并在调用存储过程后获取。
   * INOUT参数：既可以作为输入参数传入存储过程，也可以在存储过程内部修改并返回给调用者。
3. characteristics：存储过程的特性配置，可以包括以下选项：
   * LANGUAGE SQL：指定存储过程使用SQL语言。
   * LANGUAGE {SQL | \[JAVA] | \[C] | \[C++] | \[C#] }：指定存储过程使用的语言，除了SQL语言外，还可以是JAVA、C、C++或C#。
   * DETERMINISTIC：表示存储过程的结果是确定性的，即对于相同的输入参数，结果总是一样的。
   * NOT DETERMINISTIC：表示存储过程的结果是非确定性的，即对于相同的输入参数，结果可能不同。
   * CONTAINS SQL：表示存储过程包含SQL语句。
   * NO SQL：表示存储过程不包含SQL语句。
   * READS SQL DATA：表示存储过程读取数据库的数据。
   * MODIFIES SQL DATA：表示存储过程修改数据库的数据。
