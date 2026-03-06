## QUESTION-3

select s.sname, count(o.onum), avg(o.amt) from salespeople s left join orders o on o.snum=s.snum group by s.sname;

```sql


 CREATE VIEW sales_order_avg AS select s.sname, count(o.onum) as total, avg(o.amt) as amt_Avg, sum(o.amt) as total_amount from salespeople s left join orders o on o.snum=s.snum group by s.sname;
Query OK, 0 rows affected (0.01 sec)

mysql> select * from sales_order_avg;
+---------+-------+-------------+--------------+
| sname   | total | amt_Avg     | total_amount |
+---------+-------+-------------+--------------+
| Peel    |     3 | 5127.356667 |     15382.07 |
| Serres  |     3 | 1848.716667 |      5546.15 |
| Motika  |     1 | 1900.100000 |      1900.10 |
| Rifkin  |     2 |  558.425000 |      1116.85 |
| Axelrod |     1 | 1713.230000 |      1713.23 |
+---------+-------+-------------+--------------+
5 rows in set (0.00 sec)



```


## QUESTION-4

```sql

CREATE VIEW sales_customers as select s.sname as salesperson_name, c.cname as customer_name from customers c left join salespeople s on s.snum=c.snum;


select * from sales_customers;

+------------------+---------------+
| salesperson_name | customer_name |
+------------------+---------------+
| Peel             | Hoffman       |
| Axelrod          | Giovanni      |
| Serres           | Liu           |
| Serres           | Grass         |
| Peel             | Clemens       |
| Rifkin           | Cisneros      |
| Motika           | Pereira       |
+------------------+---------------+

```


## QUESTION-5

```sql



```