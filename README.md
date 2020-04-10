# mysql-final-test

2019-2020 mysql final test

姓名：邱富康

学号：17061521

说明1：考试为开卷，可以上网，自觉不要相互电话和QQ；

说明2：考试时间为：2020 年 4 月 10 日 8:10分-9:40分。

说明3：试题比较多，抓紧时间，超时提交的github commit不被接受。未避免完全超时提交，可以在做题过程中多 commit 几次。

说明4：结束后发邮件给 42225@hdu.edu.cn 标题为“MySQL期末考试,姓名+学号”，内容为github链接。


1 打印当前时间（例如 2020-04-07 13:41:42），写出SQL语句和结果
```sql
mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2020-04-10 07:57:14 |
+---------------------+
1 row in set (0.01 sec)
```

2 组合打印自己的姓名和学号

(例如 张三+123456 或者 zhangsan+123456 显示需包含加号)，写出SQL语句和结果
```sql
mysql> select CONCAT('邱富康','+','17061521');
+---------------------------------+
| CONCAT('邱富康','+','17061521') |
+---------------------------------+
| 邱富康+17061521                 |
+---------------------------------+
1 row in set (0.01 sec)
```

3 建立如下表1和表2，写出建表语句和插入语句。

表1：其中deptno为主键
```
deptno, dname,    loc
(10, "ACCOUNTING", "NEW YORK"),
(20, "RESEARCH", "DALLAS"),
(30, "SALES", "CHICAGO"),
(40, "OPERATIONS", "BOSTON")
```

```sql
mysql> use biu1;
Database changed
mysql> create table test1(
    -> deptno int PRIMARY KEY,
    -> deptno varchar(20),
    -> loc varchar(20)
    -> );
ERROR 1060 (42S21): Duplicate column name 'deptno'
mysql> create table test1(
    -> deptno int PRIMARY KEY,
    -> dname varchar(20),
    -> loc varchar(20)
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql> insert into test1()
    -> values(10,'ACCOUNTING','NEW YORK'),
    -> (20, "RESEARCH", "DALLAS"),
    -> (30, "SALES", "CHICAGO"),
    -> (40, "OPERATIONS", "BOSTON");
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> select * from test1;
+--------+------------+----------+
| deptno | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
4 rows in set (0.01 sec)
```
表2：其中empno字段为主键
```
        empno, ename,    job,    MGR,   Hiredate,    sal,   comm, deptno
        (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
	(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
	(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
	(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
	(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
	(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
	(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
	(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
	(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
	(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
	(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
```

```sql
mysql> CREATE TABLE test2(
    -> empno INT  PRIMARY KEY,
    -> ename VARCHAR(20),
    -> job  VARCHAR(20),
    -> MGR  INT,
    -> Hiredate Date,
    -> sal    float,
    -> comm   float,
    -> deptno INT NOT NULL
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql> insert into test2()
    -> values(7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
    -> (7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
    -> (7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
    -> (7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
    -> (7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
    -> (7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
    -> (7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
    -> (7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
    -> (7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
    -> (7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
    -> (7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10);
Query OK, 13 rows affected (0.01 sec)
Records: 13  Duplicates: 0  Warnings: 0

mysql> selsct * from test2;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'selsct * from test2' at line 1
mysql> select * from test2;
+-------+--------+-----------+------+------------+------+------+--------+
| empno | ename  | job       | MGR  | Hiredate   | sal  | comm | deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
13 rows in set (0.00 sec)
```
3.1 表2 中再插入一条记录：

`(你的学号，你的姓名或者拼音， “CLERK”, 7782, 你的生日,  NULL, NULL, 10)`
 
例如：`(12345,  "Zhangsan", "sTUDENT", 7782, "2000-03-12", NULL, NULL, 10)`

```sql
mysql> insert into test2()
    -> values(17061521,'QIUFUKANG','CLERK',7782,'2000-03-12',NULL,NULL,10);
Query OK, 1 row affected (0.01 sec)
#### 注：这里我的job选择了CLERK。
mysql> SELECT * FROM TEST2;
+----------+-----------+-----------+------+------------+------+------+--------+
| empno    | ename     | job       | MGR  | Hiredate   | sal  | comm | deptno |
+----------+-----------+-----------+------+------------+------+------+--------+
|     7369 | SMITH     | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     7499 | ALLEN     | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     7521 | WARD      | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     7566 | JONES     | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     7654 | MARTIN    | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     7698 | BLAKE     | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     7788 | SCOTT     | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7839 | KING      | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     7844 | TURNER    | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     7878 | ADAMS     | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     7900 | JAMES     | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     7902 | FORD      | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7934 | MILLER    | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
| 17061521 | QIUFUKANG | CLERK     | 7782 | 2000-03-12 | NULL | NULL |     10 |
+----------+-----------+-----------+------+------------+------+------+--------+
14 rows in set (0.00 sec)
```
3.2 表中入职时间（Hiredate字段）最短的人。
```sql
mysql> SELECT * FROM test2 WHERE Hiredate = (SELECT MAX(Hiredate) FROM test2);
+----------+-----------+-------+------+------------+------+------+--------+
| empno    | ename     | job   | MGR  | Hiredate   | sal  | comm | deptno |
+----------+-----------+-------+------+------------+------+------+--------+
| 17061521 | QIUFUKANG | CLERK | 7782 | 2000-03-12 | NULL | NULL |     10 |
+----------+-----------+-------+------+------------+------+------+--------+
1 row in set (0.01 sec)

+ 所有入职时间最短的人就是我！

```

3.3 有几种职位（job字段）？在关系代数中，本操作是什么运算？
```sql
mysql> select distinct job
    -> from test2;
+-----------+
| job       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
+-----------+
5 rows in set (0.01 sec)

mysql> select found_rows();
+--------------+
| found_rows() |
+--------------+
|            5 |
+--------------+
1 row in set (0.00 sec)
```
+ job字段有5个职位
+ 在关系代数中，本操作是什么运算:选择

3.4 将 MILLER 的 comm 增加 100； 然后，找到 comm 比 MILLER 低的人；
```sql
mysql> select ename from test2 WHERE sal > (
    -> select sal+100 from test2 WHERE ename='MILLER');
+--------+
| ename  |
+--------+
| ALLEN  |
| JONES  |
| BLAKE  |
| SCOTT  |
| KING   |
| TURNER |
| FORD   |
+--------+
7 rows in set (0.01 sec)

mysql> select * from test2 WHERE sal > (
    -> select sal+100 from test2 WHERE ename='MILLER');
+-------+--------+-----------+------+------------+------+------+--------+
| empno | ename  | job       | MGR  | Hiredate   | sal  | comm | deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
+-------+--------+-----------+------+------------+------+------+--------+
7 rows in set (0.00 sec)
```
3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理； 

3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？

3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。

3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？

3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引

3.10 将表2的 sal 字段改名为 salary

3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。

4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；

4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。

4.2 显示该账号权限

4.3 `with grant option` 是什么意思。

5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？

6 画出表 1 和表 2 所对应的 E-R 图

7 什么是外模式，什么是内模式。为什么要分成这几层？

8 什么是ACID？

8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；

8.2 如何查看 MySQL 当前的隔离级别？

8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？

9 有哪些场景不适合用关系型数据库？为什么？
