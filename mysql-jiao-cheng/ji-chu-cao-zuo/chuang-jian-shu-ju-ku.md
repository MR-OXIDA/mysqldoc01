# 创建数据库

### 创建数据库

使用以下命令创建数据库：

```sql
CREATE DATABASE database_name;
```

将 "database\_name" 替换为您想要创建的数据库的名称。

以下是一个完整的示例：

```sql
CREATE DATABASE mydatabase;
```

这将创建一个名为"mydatabase"的数据库。您可以根据需要更改数据库名称。

### 查看数据库定义

要查看已创建的数据库的定义，您可以使用以下步骤：

1. 打开MySQL客户端（如MySQL命令行或MySQL Workbench）。
2. 连接到MySQL服务器，输入用户名和密码（如果有）。
3.  使用以下命令列出所有数据库：

    ```sql
    SHOW DATABASES;
    ```

    这将显示所有已创建的数据库的列表。
4.  选择您想要查看定义的数据库，并使用以下命令切换到该数据库：

    ```sql
    USE database_name;
    ```

    将 "database\_name" 替换为您要查看的数据库的名称。
5.  使用以下命令显示数据库的定义：

    ```sql
    SHOW CREATE DATABASE database_name;
    ```

    将 "database\_name" 替换为您要查看的数据库的名称。
6. 执行命令后，MySQL将显示所选数据库的定义，包括创建数据库的SQL语句和其他属性。

以下是一个示例：

```sql
SHOW CREATE DATABASE mydatabase;
```

这将显示名为"mydatabase"的数据库的定义。您可以根据需要更改数据库名称。

### 列出所有数据库
