## QUESTION-1

```sql

select o.onum, c.cname from customers c inner join orders o on o.cnum=c.cnum;

+------+----------+
| onum | cname    |
+------+----------+
| 3001 | Cisneros |
| 3003 | Hoffman  |
| 3002 | Pereira  |
| 3005 | Liu      |
| 3006 | Cisneros |
| 3009 | Giovanni |
| 3007 | Grass    |
| 3008 | Clemens  |
| 3010 | Grass    |
| 3011 | Clemens  |
+------+----------+
10 rows in set (0.00 sec)

```

## QUESTION-2

```sql

select o.onum, c.cname, s.sname from orders o inner join customers c on o.cnum=c.cnum inner join salespeople s on o.snum=s.snum;

+------+----------+---------+
| onum | cname    | sname   |
+------+----------+---------+
| 3003 | Hoffman  | Peel    |
| 3009 | Giovanni | Axelrod |
| 3005 | Liu      | Serres  |
| 3010 | Grass    | Serres  |
| 3007 | Grass    | Serres  |
| 3011 | Clemens  | Peel    |
| 3008 | Clemens  | Peel    |
| 3006 | Cisneros | Rifkin  |
| 3001 | Cisneros | Rifkin  |
| 3002 | Pereira  | Motika  |
+------+----------+---------+
10 rows in set (0.00 sec)

```

## QUESTION-3

```sql

select c.cname, s.sname, s.comm from customers c inner join salespeople s on c.snum=s.snum where s.comm > 0.12;
+----------+--------+------+
| cname    | sname  | comm |
+----------+--------+------+
| Liu      | Serres | 0.13 |
| Grass    | Serres | 0.13 |
| Cisneros | Rifkin | 0.15 |
+----------+--------+------+
3 rows in set (0.01 sec)

```

## QUESTION-4

```sql

SELECT o.onum, s.comm, s.comm * o.amt FROM orders o INNER JOIN customers c ON o.cnum = c.cnum INNER JOIN salespeople s ON o.snum = s.snum WHERE c.rating > 100;

+------+------+----------------+
| onum | comm | s.comm * o.amt |
+------+------+----------------+
| 3010 | 0.13 |        40.2935 |
| 3007 | 0.13 |         9.8475 |
| 3005 | 0.13 |       670.8585 |
| 3006 | 0.15 |       164.7240 |
| 3001 | 0.15 |         2.8035 |
+------+------+----------------+
5 rows in set (0.00 sec)

```

## QUESTION-5

```sql

select s1.sname, s2.sname, s1.city from salespeople s1, salespeople s2 where s1.city=s2.city and s1.sname > s2.sname;
+-------+--------+--------+
| sname | sname  | city   |
+-------+--------+--------+
| Peel  | Motika | London |
+-------+--------+--------+
1 row in set (0.00 sec)

kd3_akram_96232>select s1.sname, s2.sname, s1.city from salespeople s1, salespeople s2 where s1.city=s2.city and s1.sname> s2.sname;

```