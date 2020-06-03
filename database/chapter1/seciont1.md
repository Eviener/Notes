# SQL 查询语法

## SELECT - 查询数据

SELECT 语句用于从表中选取数据。

```sql
select * from table_name;
select LastName,FirstName from Persons
```

## DISTINCT - 去重数据

关键词 DISTINCT 用于返回数据中唯一不同的值。

```sql
select distinct FirstName from Persons
```

## WHERE - 条件

有条件地从表中选取数据

```sql
select * from Persons where City='Beijing'
select * from Persons where Year>1965
```

**请注意，文本值用单引号''，数值不用引号**

下面的运算符可在 WHERE 子句中使用：

| **操作符** | **描述** |
| :--- | :--- |
| = | 等于 |
| &lt;&gt; | 不等于 |
| &gt; | 大于 |
| &lt; | 小于 |
| &gt;= | 大于等于 |
| &lt;= | 小于等于 |
| BETWEEN ... AND... | 在某个范围内 |
| LIKE | 模糊查询 |

