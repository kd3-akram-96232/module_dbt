## QUESTION-1

```sql

    select odate, count(distinct snum) from orders group by odate;

+------------+----------------------+
| odate      | count(distinct snum) |
+------------+----------------------+
| 1990-10-03 |                    4 |
| 1990-10-04 |                    3 |
+------------+----------------------+
2 rows in set (0.02 sec)

```

## QUESTION-2

```sql

select concat('For the city ', city, ' highest rating is: ', max(rating)) rating from customers group by city;

+----------------------------------------------+
| rating                                       |
+----------------------------------------------+
| For the city London highest rating is: 100   |
| For the city Rome highest rating is: 200     |
| For the city San Jose highest rating is: 300 |
| For the city Berlin highest rating is: 300   |
+----------------------------------------------+
4 rows in set (0.00 sec)


```


## QUESTION-3

```sql

select odate, sum(amt) from orders group by odate order by sum(amt) desc;

+------------+----------+
| odate      | sum(amt) |
+------------+----------+
| 1990-10-04 | 16713.81 |
| 1990-10-03 |  8944.59 |
+------------+----------+
2 rows in set (0.00 sec)


```


## QUESTION-4

```sql

select snum, sum(amt) from orders group by snum having sum(amt) > 2565.84;

+------+----------+
| snum | sum(amt) |
+------+----------+
| 1001 | 15382.07 |
| 1002 |  5546.15 |
+------+----------+
2 rows in set (0.01 sec)

```


## QUESTION-5

```sql

select city, max(rating) from customers group by city;
+----------+-------------+
| city     | max(rating) |
+----------+-------------+
| London   |         100 |
| Rome     |         200 |
| San Jose |         300 |
| Berlin   |         300 |
+----------+-------------+
4 rows in set (0.00 sec)

```

## QUESTION-6

```sql

select snum, max(amt) from orders group by snum having max(amt) > 3000 order by max(amt) desc;
+------+----------+
| snum | max(amt) |
+------+----------+
| 1001 |  9891.88 |
| 1002 |  5160.45 |
+------+----------+
2 rows in set (0.00 sec)

```

### QUESTION-7

```sql

select cnum, min(amt) from orders group by cnum order by cnum;

+------+----------+
| cnum | min(amt) |
+------+----------+
| 2001 |   767.19 |
| 2002 |  1713.23 |
| 2003 |  5160.45 |
| 2004 |    75.75 |
| 2006 |  4723.00 |
| 2007 |  1900.10 |
| 2008 |    18.69 |
+------+----------+
7 rows in set (0.00 sec)

```