## QUESTION-1

1.  Create an index that will enable a user to pull orders for  
    ‘1990-10-03’ out of the Orders table quickly.

```sql

create index idx_order_date on orders(odate);

select * from orders where odate='1990-10-03';


```

## QUESTION-2

If the Orders table has already been created, how can you force the  
   onum field to be unique (assume all current values are unique)?

```sql

create unique index idx_orders_onum on orders(onum);


```

## QUESTION-3

. Create an index that would permit salesperson to retrieve his orders

```sql

create index idx_orders_snum on orders(snum, odate);
-- create index idx_salespeople_snum on salespeople(snum);

```

## QUESTION-4

4.  Let us assume that each salesperson is to have only one customer 
of a given rating, and this is currently the case. Create an index that enforces it.

```sql

create index idx_customers_rating on customers(snum, rating);

```

## QUESTION-5

Create an index to speed up searching order on a given date by given 
customer. 

```sql

 create index idx_order_custome_date on orders(cnum, odate);

```