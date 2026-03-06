## QUESTION-1

```sql

DELIMITER $$

CREATE PROCEDURE get_ractangle(w INT, l INT)
BEGIN
DECLARE area INT;
DECLARE perimeter INT;
SET area = w * l;
SET perimeter = 2 * (w * l);

SELECT area, perimeter;
END;
$$

DELIMITER ;

-- output --

call get_ractangle(5, 5);   

+------+-----------+
| area | perimeter |
+------+-----------+
|   25 |        50 |
+------+-----------+
1 row in set (0.00 sec)

```


## QUESTION-2

Write a procedure that declares an integer variable called num, assigns
a value to it, computes and inserts into the temp table the value of the
variable itself, its square, and its cube.

```sql

DELIMITER $$

CREATE PROCEDURE two(p_num INT)

BEGIN

DECLARE cube1 INT;
DECLARE square INT;

SET cube1 = p_num * p_num;
SET square = p_num * p_num * p_num;

INSERT INTO temp_table VALUES(cube1), (square);

select cube1, square;

END;

$$ 
DELIMITER ;

--output---

call two(10);
+-------+--------+
| cube1 | square |
+-------+--------+
|   100 |   1000 |
+-------+--------+
1 row in set (0.01 sec)

Query OK, 0 rows affected (0.01 sec)


```




## QUESTION-3
Create a procedure to Convert a temperature in Fahrenheit (F) to its
equivalent in Celsius (C) and vice versa. The required formulae are
C= (F-32) *5/9 F= 9/5*C + 32

```sql

DELIMITER $$

CREATE PROCEDURE three (c INT, f INT)

BEGIN

DECLARE toCelcius INT DEFAULT (f-32) * (5/9);
DECLARE toFahrenheit INT DEFAULT ((9/5)*c) + 32;

select toCelcius, toFahrenheit;

END;

$$

DELIMITER ;

call three(10, 20); -- 10 = celcius, 20 = fahrenheit
+-----------+--------------+
| toCelcius | toFahrenheit |
+-----------+--------------+
|        -7 |           50 |
+-----------+--------------+
1 row in set (0.00 sec)

Query OK, 0 rows affected (0.00 sec)


```


## QUESTION-4

Create a procedure to Convert a number of inches into yards, feet, and
inches. For example, 124 inches equals 3 yards, 1 foot, and 4 inches

```sql

DELIMITER $$
CREATE PROCEDURE four(inch INT)
BEGIN
    DECLARE yard INT;
    DECLARE yard_remainder INT;
    DECLARE foot INT;
    DECLARE foot_reminder INT;

    SET yard = inch / 36;
    SET yard_remainder = inch % 36;

    SET foot = yard_remainder / 12;
    SET foot_reminder = yard_remainder % 12;

    SELECT inch as total, yard, foot, foot_reminder;
END;
$$
DELIMITER ;

call four(124);
+-------+------+------+--------+
| total | yard | foot | inches |
+-------+------+------+--------+
|   124 |    3 |    1 |      4 |
+-------+------+------+--------+
1 row in set (0.00 sec)



```

## QUESTION-5

Create a procedure to read two real numbers and tell whether the
product (multiply) of the two numbers is equal to or greater than 100.

```sql

DELIMITER $$
CREATE PROCEDURE five(r1 INT, r2 INT)

BEGIN
    DECLARE result INT;

    SET result = r1 * r2;

    IF result > 100 THEN

        SELECT 'GREATOR' as result;

    ELSE 

        SELECT 'LESSTHAN' as result;

    END IF;

END;

$$

DELIMITER ;

--output

call five(10, 20);
+---------+
| result  |
+---------+
| GREATOR |
+---------+
1 row in set (0.00 sec)


```