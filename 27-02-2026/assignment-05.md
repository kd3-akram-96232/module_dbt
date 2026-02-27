## QUESTION-1

```sql

    select concat(LOWER(first_name), '-' , UPPER(last_name)) as full_name from employees;

+-------------------+
| full_name         |
+-------------------+
| ellen-ABEL        |
| sundar-ANDE       |
| mozhe-ATKINSON    |
| shelli-BAIDA      |
| amit-BANDA        |
| elizabeth-BATES   |
| sarah-BELL        |
| david-BERNSTEIN   |
| laura-BISSOT      |
| harrison-BLOOM    |
| hermann-BROWN     |
| alexis-BULL       |
| anthony-CABRIO    |
| gerald-CAMBRAULT  |
| nanette-CAMBRAULT |
| john-CHEN         |
| kelly-CHUNG       |
| karen-COLMENARES  |
| curtis-DAVIES     |
| pat-DAVIS         |
| julia-DELLINGER   |
| jennifer-DILLY    |
| louise-DORAN      |
| alberto-ERRAZURIZ |
| britney-EVERETT   |
| daniel-FAVIET     |
| kevin-FEENEY      |
| jean-FLEAUR       |
| tayler-FOX        |
| adam-FRIPP        |
| lex-GARCIA        |
| ki-GEE            |
| girard-GEONI      |
| william-GIETZ     |
| douglas-GRANT     |
| kimberely-GRANT   |
| danielle-GREENE   |
| nancy-GRUENBERG   |
| peter-HALL        |
| shelley-HIGGINS   |
| guy-HIMURO        |
| alyssa-HUTTON     |
| valli-JACKSON     |
| susan-JACOBS      |
| alexander-JAMES   |
| charles-JOHNSON   |
| vance-JONES       |
| payam-KAUFLING    |
| alexander-KHOO    |
| janette-KING      |
| steven-KING       |
| sundita-KUMAR     |
| renske-LADWIG     |
| james-LANDRY      |
| david-LEE         |
| den-LI            |
| jack-LIVINGSTON   |
| jason-MALLIN      |
| steven-MARKLE     |
| james-MARLOW      |
| michael-MARTINEZ  |
| mattea-MARVINS    |
| randall-MATOS     |
| allan-MCEWEN      |
| samuel-MCLEOD     |
| irene-MIKKILINENI |
| bruce-MILLER      |
| kevin-MOURGOS     |
| julia-NAYER       |
| diana-NGUYEN      |
| donald-OCONNELL   |
| christopher-OLSEN |
| tj-OLSON          |
| lisa-OZER         |
| karen-PARTNERS    |
| joshua-PATEL      |
| randall-PERKINS   |
| hazel-PHILTANKER  |
| luis-POPP         |
| trenna-RAJS       |
| michael-ROGERS    |
| nandita-SARCHAND  |
| ismael-SCIARRA    |
| john-SEO          |
| sarath-SEWALL     |
| john-SINGH        |
| lindsey-SMITH     |
| william-SMITH     |
| stephen-STILES    |
| martha-SULLIVAN   |
| patrick-SULLY     |
| jonathon-TAYLOR   |
| winston-TAYLOR    |
| sigal-TOBIAS      |
| sean-TUCKER       |
| oliver-TUVAULT    |
| jose manuel-URMAN |
| peter-VARGAS      |
| timothy-VENZL     |
| clara-VISHNEY     |
| shanta-VOLLMAN    |
| alana-WALSH       |
| matthew-WEISS     |
| jennifer-WHALEN   |
| david-WILLIAMS    |
| neena-YANG        |
| eleni-ZLOTKEY     |
+-------------------+
107 rows in set (0.00 sec)

```


## QUESTION-2

```sql

select SUBSTRING_INDEX(job_title, ' ', 1) from jobs;

+------------------------------------+
| SUBSTRING_INDEX(job_title, ' ', 1) |
+------------------------------------+
| Public                             |
| Accounting                         |
| Administration                     |
| President                          |
| Administration                     |
| Accountant                         |
| Finance                            |
| Human                              |
| Programmer                         |
| Marketing                          |
| Marketing                          |
| Public                             |
| Purchasing                         |
| Purchasing                         |
| Sales                              |
| Sales                              |
| Shipping                           |
| Stock                              |
| Stock                              |
+------------------------------------+
19 rows in set (0.00 sec)

```

## QUESTION-3

```sql

select first_name, last_name, LENGTH(first_name) from employees where last_name LIKE '___%b%';

+------------+-----------+--------------------+
| first_name | last_name | LENGTH(first_name) |
+------------+-----------+--------------------+
| Gerald     | Cambrault |                  6 |
| Nanette    | Cambrault |                  7 |
| Nancy      | Gruenberg |                  5 |
| Susan      | Jacobs    |                  5 |
+------------+-----------+--------------------+
4 rows in set (0.01 sec)

```

## QUESTION-4

```sql

select employee_id, first_name, last_name from employees where first_name like '% %' OR last_name like '% %';

+-------------+-------------+-----------+
| employee_id | first_name  | last_name |
+-------------+-------------+-----------+
|         112 | Jose Manuel | Urman     |
+-------------+-------------+-----------+
1 row in set (0.00 sec)

```

## QUESTION-5

```sql

select first_name, salary, ROUND(salary, -3) from employees limit 5;
+------------+----------+-------------------+
| first_name | salary   | ROUND(salary, -3) |
+------------+----------+-------------------+
| Steven     | 24000.00 |             24000 |
| Neena      | 17000.00 |             17000 |
| Lex        | 17000.00 |             17000 |
| Alexander  |  9000.00 |              9000 |
| Bruce      |  6000.00 |              6000 |
+------------+----------+-------------------+
5 rows in set (0.01 sec)

```

## QUESTION-6

```sql

select employee_id, end_date, concat(DATE_FORMAT(end_date, '%W'), ',' , DATE_FORMAT(end_date, '%b'), ' ', DATE_FORMAT(end_date, '%d'), 'th ', DATE_FORMAT(end_date, '%Y') ) as job_end_date from job_history;

+-------------+------------+------------------------+
| employee_id | end_date   | job_end_date           |
+-------------+------------+------------------------+
|         101 | 2011-10-27 | Thursday,Oct 27th 2011 |
|         101 | 2015-03-15 | Sunday,Mar 15th 2015   |
|         102 | 2016-07-24 | Sunday,Jul 24th 2016   |
|         114 | 2017-12-31 | Sunday,Dec 31th 2017   |
|         122 | 2017-12-31 | Sunday,Dec 31th 2017   |
|         176 | 2016-12-31 | Saturday,Dec 31th 2016 |
|         176 | 2017-12-31 | Sunday,Dec 31th 2017   |
|         200 | 2011-06-17 | Friday,Jun 17th 2011   |
|         200 | 2016-12-31 | Saturday,Dec 31th 2016 |
|         201 | 2017-12-19 | Tuesday,Dec 19th 2017  |
+-------------+------------+------------------------+
10 rows in set (0.00 sec)

```

## QUESTION-7

```sql



```