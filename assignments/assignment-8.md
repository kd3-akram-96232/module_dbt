## QUESTION-1

```sql

select o.onum, o.amt, o.odate, o.cnum, o.snum from customers e inner join orders o on e.cnum = o.cnum where e.cname='Cisneros';

+------+---------+------------+------+------+
| onum | amt     | odate      | cnum | snum |
+------+---------+------------+------+------+
| 3001 |   18.69 | 1990-10-03 | 2008 | 1007 |
| 3006 | 1098.16 | 1990-10-03 | 2008 | 1007 |
+------+---------+------------+------+------+
2 rows in set (0.00 sec)

```

## QUESTION-2

```sql

select o.amt, c.cname, c.rating from customers c inner join orders o on o.cnum=c.cnum where o.amt > (select avg(amt) from orders);
+---------+---------+--------+
| amt     | cname   | rating |
+---------+---------+--------+
| 5160.45 | Liu     |    200 |
| 9891.88 | Clemens |    100 |
| 4723.00 | Clemens |    100 |
+---------+---------+--------+
3 rows in set (0.00 sec)

```

## QUESTION-3

```sql

select snum, sum(amt) from orders group by snum having sum(amt) > (select max(amt) from orders);
+------+----------+
| snum | sum(amt) |
+------+----------+
| 1001 | 15382.07 |
+------+----------+
1 row in set (0.00 sec)

```

## QUESTION-4

```sql

select * from customers where rating >= any(select rating from customers where snum = (select snum from salespeople where sname = 'Serres'));
+------+----------+----------+--------+------+
| cnum | cname    | city     | rating | snum |
+------+----------+----------+--------+------+
| 2002 | Giovanni | Rome     |    200 | 1003 |
| 2003 | Liu      | San Jose |    200 | 1002 |
| 2004 | Grass    | Berlin   |    300 | 1002 |
| 2008 | Cisneros | San Jose |    300 | 1007 |
+------+----------+----------+--------+------+
4 rows in set (0.00 sec)

```

## QUESTION-5

```sql

select s.sname, s.snum, s.city from salespeople s where s.city != ALL(select city from customers where s.snum=customers.snum);
+---------+------+-----------+
| sname   | snum | city      |
+---------+------+-----------+
| Motika  | 1004 | London    |
| Rifkin  | 1007 | Barcelona |
| Axelrod | 1003 | New York  |
+---------+------+-----------+
3 rows in set (0.00 sec)

```

## QUESTION-6

```sql

select oo.onum, oo.amt, oo.odate, oo.cnum, oo.snum from orders oo where oo.amt > any(select o.amt from orders o where o.cnum = any(select cnum from customers where o.cnum=cnum and city='London'));

+------+---------+------------+------+------+
| onum | amt     | odate      | cnum | snum |
+------+---------+------------+------+------+
| 3002 | 1900.10 | 1990-10-03 | 2007 | 1004 |
| 3005 | 5160.45 | 1990-10-03 | 2003 | 1002 |
| 3006 | 1098.16 | 1990-10-03 | 2008 | 1007 |
| 3009 | 1713.23 | 1990-10-04 | 2002 | 1003 |
| 3008 | 4723.00 | 1990-10-04 | 2006 | 1001 |
| 3011 | 9891.88 | 1990-10-04 | 2006 | 1001 |
+------+---------+------------+------+------+
6 rows in set (0.00 sec)

```

## QUESTION-7

```sql

select * from orders where snum = any(select snum from salespeople where sname='Motika');
+------+---------+------------+------+------+
| onum | amt     | odate      | cnum | snum |
+------+---------+------------+------+------+
| 3002 | 1900.10 | 1990-10-03 | 2007 | 1004 |
+------+---------+------------+------+------+
1 row in set (0.00 sec)

```

## QUESTION-8

```sql

select * from orders o where o.snum = all(select snum from customers where city='London');
+------+---------+------------+------+------+
| onum | amt     | odate      | cnum | snum |
+------+---------+------------+------+------+
| 3003 |  767.19 | 1990-10-03 | 2001 | 1001 |
| 3008 | 4723.00 | 1990-10-04 | 2006 | 1001 |
| 3011 | 9891.88 | 1990-10-04 | 2006 | 1001 |
+------+---------+------------+------+------+
3 rows in set (0.00 sec)

```

## QUESTION-9

```sql

select s.sname, s.snum from salespeople s where 1 < (select count(*) from customers c where s.snum=c.snum);
+--------+------+
| sname  | snum |
+--------+------+
| Peel   | 1001 |
| Serres | 1002 |
+--------+------+
2 rows in set (0.00 sec)

```

## QUESTION-10

```sql

s.sname, s.snum, s.city, (select count(*) from customers c where s.snum=c.snum) as customer_count from salespeople s where 1 < (select count(*) from customers c where s.snum=c.snum);
+--------+------+----------+----------------+
| sname  | snum | city     | customer_count |
+--------+------+----------+----------------+
| Peel   | 1001 | London   |              2 |
| Serres | 1002 | San Jose |              2 |
+--------+------+----------+----------------+
2 rows in set (0.00 sec)

```

## QUESTION-11

```sql

select c.cnum, c.cname, c.city,  c.rating, c.snum from customers c where c.rating > any(select rating from customers where city = 'ROME');
+------+----------+----------+--------+------+
| cnum | cname    | city     | rating | snum |
+------+----------+----------+--------+------+
| 2002 | Giovanni | Rome     |    200 | 1003 |
| 2003 | Liu      | San Jose |    200 | 1002 |
| 2004 | Grass    | Berlin   |    300 | 1002 |
| 2008 | Cisneros | San Jose |    300 | 1007 |
+------+----------+----------+--------+------+
4 rows in set (0.00 sec)

```

## QUESTION-12

```sql

select o.onum, o.amt, o.odate, o.cnum, o.snum from orders o where o.amt > (select min(amt) from orders where odate = '1990-10-04');
+------+---------+------------+------+------+
| onum | amt     | odate      | cnum | snum |
+------+---------+------------+------+------+
| 3003 |  767.19 | 1990-10-03 | 2001 | 1001 |
| 3002 | 1900.10 | 1990-10-03 | 2007 | 1004 |
| 3005 | 5160.45 | 1990-10-03 | 2003 | 1002 |
| 3006 | 1098.16 | 1990-10-03 | 2008 | 1007 |
| 3009 | 1713.23 | 1990-10-04 | 2002 | 1003 |
| 3008 | 4723.00 | 1990-10-04 | 2006 | 1001 |
| 3010 |  309.95 | 1990-10-04 | 2004 | 1002 |
| 3011 | 9891.88 | 1990-10-04 | 2006 | 1001 |
+------+---------+------------+------+------+
8 rows in set (0.00 sec)

```

## QUESTION-13

```sql

select oo.onum, oo.amt, oo.odate, oo.cnum, oo.snum from orders oo where oo.amt < any(select o.amt from orders o where o.cnum = any(select c.cnum from customers c where c.city = 'San Jose'));        
+------+---------+------------+------+------+
| onum | amt     | odate      | cnum | snum |
+------+---------+------------+------+------+
| 3001 |   18.69 | 1990-10-03 | 2008 | 1007 |
| 3003 |  767.19 | 1990-10-03 | 2001 | 1001 |
| 3002 | 1900.10 | 1990-10-03 | 2007 | 1004 |
| 3006 | 1098.16 | 1990-10-03 | 2008 | 1007 |
| 3009 | 1713.23 | 1990-10-04 | 2002 | 1003 |
| 3007 |   75.75 | 1990-10-04 | 2004 | 1002 |
| 3008 | 4723.00 | 1990-10-04 | 2006 | 1001 |
| 3010 |  309.95 | 1990-10-04 | 2004 | 1002 |
+------+---------+------------+------+------+
8 rows in set (0.00 sec)

```

## QUESTION-14

```sql

select * from customers c where c.rating > (select max(rating) from customers where city='London');
+------+----------+----------+--------+------+
| cnum | cname    | city     | rating | snum |
+------+----------+----------+--------+------+
| 2002 | Giovanni | Rome     |    200 | 1003 |
| 2003 | Liu      | San Jose |    200 | 1002 |
| 2004 | Grass    | Berlin   |    300 | 1002 |
| 2008 | Cisneros | San Jose |    300 | 1007 |
+------+----------+----------+--------+------+
4 rows in set (0.00 sec)

```