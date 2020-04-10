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
mysql> select * from test2 WHERE sal < (
    -> select sal+100 from test2 WHERE ename='MILLER');
+-------+--------+----------+------+------------+------+------+--------+
| empno | ename  | job      | MGR  | Hiredate   | sal  | comm | deptno |
+-------+--------+----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK    | 7902 | 1981-03-12 |  800 | NULL |     20 |
|  7521 | WARD   | SALESMAN | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|  7878 | ADAMS  | CLERK    | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-03-12 |  950 | NULL |     30 |
|  7934 | MILLER | CLERK    | 7782 | 1981-03-12 | 1300 | NULL |     10 |
+-------+--------+----------+------+------------+------+------+--------+
6 rows in set (0.00 sec)

mysql> select ename from test2 WHERE sal < (
    -> select sal+100 from test2 WHERE ename='MILLER');
+--------+
| ename  |
+--------+
| SMITH  |
| WARD   |
| MARTIN |
| ADAMS  |
| JAMES  |
| MILLER |
+--------+
6 rows in set (0.00 sec)
```
3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理； 
```sql
mysql> select ename,sal+comm,count(ename) counts,AVG(sal+comm) average_sal_comm from test2;
+-------+----------+--------+------------------+
| ename | sal+comm | counts | average_sal_comm |
+-------+----------+--------+------------------+
| SMITH |     NULL |     14 |             1950 |
+-------+----------+--------+------------------+
1 row in set (0.01 sec)

mysql> select ename,coalesce(sal+comm,0),count(ename),coalesce(AVG(sal+comm),0) from test2;
+-------+----------------------+--------------+---------------------------+
| ename | coalesce(sal+comm,0) | count(ename) | coalesce(AVG(sal+comm),0) |
+-------+----------------------+--------------+---------------------------+
| SMITH |                    0 |           14 |                      1950 |
+-------+----------------------+--------------+---------------------------+
1 row in set (0.00 sec)

```
3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？
```sql
mysql> select t1.ename My_b_b_name,t2.ename My_b_name ,t3.ename My_name
    -> from (test2 t1 inner join test2 t2 on t1. empno= t2. mgr)  inner join test2 t3
    -> on t2.empno = t3.mgr;
+-------------+-----------+---------+
| My_b_b_name | My_b_name | My_name |
+-------------+-----------+---------+
| JONES       | FORD      | SMITH   |
| KING        | BLAKE     | ALLEN   |
| KING        | BLAKE     | WARD    |
| KING        | BLAKE     | MARTIN  |
| KING        | JONES     | SCOTT   |
| JONES       | SCOTT     | ADAMS   |
| KING        | BLAKE     | JAMES   |
| KING        | JONES     | FORD    |
+-------------+-----------+---------+
8 rows in set (0.01 sec)
```
+ 本操作使用关系代数中是：交
3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。
```sql
mysql> select * from test1 t1 inner join test2 t2 on t1.deptno=t2.deptno;
+--------+------------+----------+----------+-----------+-----------+------+------------+------+------+--------+
| deptno | dname      | loc      | empno    | ename     | job       | MGR  | Hiredate   | sal  | comm | deptno |
+--------+------------+----------+----------+-----------+-----------+------+------------+------+------+--------+
|     20 | RESEARCH   | DALLAS   |     7369 | SMITH     | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     30 | SALES      | CHICAGO  |     7499 | ALLEN     | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     30 | SALES      | CHICAGO  |     7521 | WARD      | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     20 | RESEARCH   | DALLAS   |     7566 | JONES     | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     30 | SALES      | CHICAGO  |     7654 | MARTIN    | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     10 | ACCOUNTING | NEW YORK |     7698 | BLAKE     | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     20 | RESEARCH   | DALLAS   |     7788 | SCOTT     | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     10 | ACCOUNTING | NEW YORK |     7839 | KING      | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     30 | SALES      | CHICAGO  |     7844 | TURNER    | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     20 | RESEARCH   | DALLAS   |     7878 | ADAMS     | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     30 | SALES      | CHICAGO  |     7900 | JAMES     | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     20 | RESEARCH   | DALLAS   |     7902 | FORD      | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     10 | ACCOUNTING | NEW YORK |     7934 | MILLER    | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
|     10 | ACCOUNTING | NEW YORK | 17061521 | QIUFUKANG | CLERK     | 7782 | 2000-03-12 | NULL | NULL |     10 |
+--------+------------+----------+----------+-----------+-----------+------+------------+------+------+--------+
14 rows in set (0.01 sec)

mysql> create view view_test1_test2
    -> as
    -> select empno,ename,job,loc from test1 t1 inner join test2 t2 on t1.deptno=t2.deptno;
Query OK, 0 rows affected (0.01 sec)

mysql> select * from view_test1_test2;
+----------+-----------+-----------+----------+
| empno    | ename     | job       | loc      |
+----------+-----------+-----------+----------+
|     7369 | SMITH     | CLERK     | DALLAS   |
|     7499 | ALLEN     | SALESMAN  | CHICAGO  |
|     7521 | WARD      | SALESMAN  | CHICAGO  |
|     7566 | JONES     | MANAGER   | DALLAS   |
|     7654 | MARTIN    | SALESMAN  | CHICAGO  |
|     7698 | BLAKE     | MANAGER   | NEW YORK |
|     7788 | SCOTT     | ANALYST   | DALLAS   |
|     7839 | KING      | PRESIDENT | NEW YORK |
|     7844 | TURNER    | SALESMAN  | CHICAGO  |
|     7878 | ADAMS     | CLERK     | DALLAS   |
|     7900 | JAMES     | CLERK     | CHICAGO  |
|     7902 | FORD      | ANALYST   | DALLAS   |
|     7934 | MILLER    | CLERK     | NEW YORK |
| 17061521 | QIUFUKANG | CLERK     | NEW YORK |
+----------+-----------+-----------+----------+
14 rows in set (0.00 sec)
```
+ 建立本视图的目的：为了提高复杂SQL语句的复用性和表操作的安全性,MySQL数据库管理系统提供了视图特性。所谓视图，本质上是一种虚拟表，其内容与真实的表相似，包含系列带有名称的列和行数据。但是，视图并不在数据库中以存储的数据值形式存在。行和列数据来自定义视图的查询所引用基本表，并且在具体引用视图时动态生成。视图使程序员只关心感兴趣的某些特定数据和他们所负责的特定任务。这样程序员只能看到视图中所定义的数据，而不是视图所引用表中的数据，从而提高了数据库中数据的安全性。

3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？
+ 这称做数据的完整性。
3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引
```sql
mysql> create unique index index_ename
    -> on test2(ename);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

```
+ 这样主要是为了提高从表中检索数据的速度。

3.10 将表2的 sal 字段改名为 salary
```sql
mysql> alter table test2
    -> change sal salary float;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc test2;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| empno    | int(11)     | NO   | PRI | NULL    |       |
| ename    | varchar(20) | YES  |     | NULL    |       |
| job      | varchar(20) | YES  |     | NULL    |       |
| MGR      | int(11)     | YES  |     | NULL    |       |
| Hiredate | date        | YES  |     | NULL    |       |
| salary   | float       | YES  |     | NULL    |       |
| comm     | float       | YES  |     | NULL    |       |
| deptno   | int(11)     | NO   |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
8 rows in set (0.00 sec)
```
3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。
```sql
mysql> DELIMITER $$
mysql> CREATE FUNCTION func_get_deptno_from_empno (empno INT)
    -> RETURNS int
    -> BEGIN
    ->     RETURN (SELECT deptno FROM test2 WHERE test2.empno = empno);
    -> END$$
Query OK, 0 rows affected (0.01 sec)

mysql> DELIMITER ;
mysql>
mysql> SELECT func_get_deptno_from_empno (7369);
+-----------------------------------+
| func_get_deptno_from_empno (7369) |
+-----------------------------------+
|                                20 |
+-----------------------------------+
1 row in set (0.01 sec)

mysql> select * from test2;
+----------+-----------+-----------+------+------------+--------+------+--------+
| empno    | ename     | job       | MGR  | Hiredate   | salary | comm | deptno |
+----------+-----------+-----------+------+------------+--------+------+--------+
|     7369 | SMITH     | CLERK     | 7902 | 1981-03-12 |    800 | NULL |     20 |
|     7499 | ALLEN     | SALESMAN  | 7698 | 1982-03-12 |   1600 |  300 |     30 |
|     7521 | WARD      | SALESMAN  | 7698 | 1838-03-12 |   1250 |  500 |     30 |
|     7566 | JONES     | MANAGER   | 7839 | 1981-03-12 |   2975 | NULL |     20 |
|     7654 | MARTIN    | SALESMAN  | 7698 | 1981-01-12 |   1250 | 1400 |     30 |
|     7698 | BLAKE     | MANAGER   | 7839 | 1985-03-12 |   2450 | NULL |     10 |
|     7788 | SCOTT     | ANALYST   | 7566 | 1981-03-12 |   3000 | NULL |     20 |
|     7839 | KING      | PRESIDENT | NULL | 1981-03-12 |   5000 | NULL |     10 |
|     7844 | TURNER    | SALESMAN  | 7689 | 1981-03-12 |   1500 |    0 |     30 |
|     7878 | ADAMS     | CLERK     | 7788 | 1981-03-12 |   1100 | NULL |     20 |
|     7900 | JAMES     | CLERK     | 7698 | 1981-03-12 |    950 | NULL |     30 |
|     7902 | FORD      | ANALYST   | 7566 | 1981-03-12 |   3000 | NULL |     20 |
|     7934 | MILLER    | CLERK     | 7782 | 1981-03-12 |   1300 | NULL |     10 |
| 17061521 | QIUFUKANG | CLERK     | 7782 | 2000-03-12 |   NULL | NULL |     10 |
+----------+-----------+-----------+------+------------+--------+------+--------+
14 rows in set (0.00 sec)
```
+ 对于存储过程来说可以返回参数，如记录集，而函数只能返回值或者表对象。函数只能返回一个变量；而存储过程可以返回多个。存储过程的参数可以有IN,OUT,INOUT三种类型，而函数只能有IN类存储过程声明时不需要返回类型，而函数声明时需要描述返回类型，且函数体中必须包含一个有效的RETURN语句。
+ 存储过程，可以使用非确定函数，不允许在用户定义函数主体中内置非确定函数。
+ 存储过程一般是作为一个独立的部分来执行（ EXECUTE 语句执行），而函数可以作为查询语句的一个部分来调用（SELECT调用），由于函数可以返回一个表对象，因此它可以在查询语句中位于FROM关键字的后面。 SQL语句中不可用存储过程，而可以使用函数。

4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；
```sql
mysql> create user`QIUFUKANG`@`*` identified by'17061521';
Query OK, 0 rows affected (0.01 sec)
```

4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。
```sql
mysql> GRANT select,insert,update ON biu1.test1 TO `QIUFUKANG`@`*`;
Query OK, 0 rows affected (0.01 sec)
```
4.2 显示该账号权限

```sql
mysql> show grants for `QIUFUKANG`@`*`
    -> ;
+-------------------------------------------------------------------+
| Grants for QIUFUKANG@*                                            |
+-------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'QIUFUKANG'@'*'                             |
| GRANT SELECT, INSERT, UPDATE ON `biu1`.`test1` TO 'QIUFUKANG'@'*' |
+-------------------------------------------------------------------+
2 rows in set (0.00 sec)
```
4.3 `with grant option` 是什么意思。

+ 用以上命令授权的用户可以给其他用户授权。

5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？
+ 表一符合第一范式和第二范式。因为第一个表的关系中的每个属性都不可再分，满足第一范式；只要表中的一个属性确定了其他的属性也随之确定了，所以满足第二范式。
+ 表二符合第一范式，但不符合第二范式。因为第一个表的关系中的每个属性都不可再分，满足第一范式；但当表中的MGR属性确定了不能确定其他的属性，所以不满足第二范式。

6 画出表 1 和表 2 所对应的 E-R 图

+ 表 1 和表 2 所对应的 E-R 图

![](https://github.com/BiubiuOoo/mysql-final-test/blob/master/E-R.PNG?raw=true)

7 什么是外模式，什么是内模式。为什么要分成这几层？
+ 外模式：也称子模式(Subschema)或用户模式，是数据库用户(包括应用程序员和最终用户)能够看见和使用的局部数据的逻辑结构和特征的描述，是数据库用户的数据视图，是与某一应用有关的数据的逻辑表示。
+ 内模式：也称存储模式(Storage Schema)，它是数据物理结构和存储方式的描述，是数据在数据库内部的表示方式(例如，记录的存储方式是顺序存储、按照B树结构存储还是按hash方法存储;索引按照什么方式组织;数据是否压缩存储，是否加密;数据的存储记录结构有何规定)。
+ 数据库的三级模式是数据库在三个级别 (层次)上的抽象，使用户能够逻辑地、抽象地处理数据而不必关心数据在计算机中的物理表示和存储。实际上 ，对于一个数据库系统而言一有物理级数据库是客观存在的，它是进行数据库操作的基础，概念级数据库中不过是物理数据库的一种逻辑的、抽象的描述(即模式)，用户级数据库则是用户与数据库的接口，它是概念级数据库的一个子集(外模式)。
+ 用户应用程序根据外模式进行数据操作，通过外模式一模式映射，定义和建立某个外模式与模式间的对应关系，将外模式与模式联系起来，当模式发生改变时，只要改变其映射，就可以使外模式保持不变，对应的应用程序也可保持不变；另一方面，通过模式一内模式映射，定义建立数据的逻辑结构(模式)与存储结构(内模式)间的对应关系，当数据的存储结构发生变化时，只需改变模式一内模式映射，就能保持模式不变，因此应用程序也可以保持不变。
8 什么是ACID？
+ ACID 一般是指数据库事务的ACID。
+ 1.Atomicity 原子性，指的是整个事务是一个独立的单元，要么操作成功，要么操作不成功

+ 2.Consistency 一致性，事务必须要保持和系统处于一致的状态（如果不一致会导致系统其它的方出现bug）

+ 3.Isolation 隔离性，事务是并发控制机制，他们的交错也需要一致性，隔离隐藏，一般通过悲观或者乐观锁实现

+ 4.Durability 耐久性，一个成功的事务将永久性地改变系统的状态，所以在它结束之前，所有导致状态的变化都记录在一个持久的事务日志中
            
8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；

8.2 如何查看 MySQL 当前的隔离级别？

+ 1.选择数据库,查看当前事务隔离界别
```sql
mysql> select @@tx_isolation;
+-----------------+
| @@tx_isolation  |
+-----------------+
| REPEATABLE-READ |
+-----------------+
1 row in set, 1 warning (0.00 sec)
```
+ 2.开启事务,回滚事务
+ 3.事务级别中脏读,幻读 
+ 4.MySQL事务autocommit设置,每次sql必须用commit提交生效.
+ MySQL默认操作模式就是autocommit自动提交模式。这就表示除非显式地开始一个事务，否则每个查询都被当做一个单独的事务自动执行。我们可以通过设置autocommit的值改变是否是自动提交autocommit模式。
+ 通过以下命令可以查看当前autocommit模式
```sql
show variables like 'autocommit';
 ```
+ 关闭自动提交,每次sql必须通过commit命令提交.
```sql
mysql> set autocommit = 0;
```
8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？

9 有哪些场景不适合用关系型数据库？为什么？
+ 如果数据量较小，那么使用关系型数据库即可，因为这个时候读写的IO瓶颈显现不出来。如果数据量较大，这时，可能对于关系型数据库来说，单表的大小就可以达到几GB，这时K-V存储的非关系型数据库的优势就体现出来了。比如现在的互联网公司，倾向于使用Nosql作为缓存，存储热数据，使用关系型数据库存储冷数据。

