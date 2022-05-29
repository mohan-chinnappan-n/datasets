# Explaining Joins using Postgresql

## Create table and data
```
mchinnappan=# create table sweet_grade (name varchar(32), score int);
CREATE TABLE
mchinnappan=# insert into sweet_grade (name, score) values ('Plum', 4), ('Mango', 4), ('Apple',3), ('Peach', 4), ('Banana', 4), ('Dates', 5);
INSERT 0 6
mchinnappan=# \d sweet_grade 
                   Table "public.sweet_grade"
 Column |         Type          | Collation | Nullable | Default 
--------+-----------------------+-----------+----------+---------
 name   | character varying(32) |           |          | 
 score  | integer               |           |          | 

mchinnappan=# select * from sweet_grade ;
  name  | score 
--------+-------
 Plum   |     4
 Mango  |     4
 Apple  |     3
 Peach  |     4
 Banana |     4
 Dates  |     5
(6 rows)

mchinnappan=# create table health_grade (name varchar(32), score int);
CREATE TABLE
mchinnappan=# insert into health_grade (name, score) values ('Mango', 5), ('Apple',5), ('Peach', 4), ('Banana', 4), ('Dates', 5), ('Jackfruit',4), ('Pear', 4);
INSERT 0 7
mchinnappan=# select * from health_grade ;
   name    | score 
-----------+-------
 Mango     |     5
 Apple     |     5
 Peach     |     4
 Banana    |     4
 Dates     |     5
 Jackfruit |     4
 Pear      |     4
(7 rows)
```

## INNER JOIN
```
mchinnappan=# SELECT * FROM sweet_grade
mchinnappan-#   INNER JOIN health_grade ON
mchinnappan-#        sweet_grade.name = health_grade.name;
  name  | score |  name  | score 
--------+-------+--------+-------
 Mango  |     4 | Mango  |     5
 Apple  |     3 | Apple  |     5
 Peach  |     4 | Peach  |     4
 Banana |     4 | Banana |     4
 Dates  |     5 | Dates  |     5
(5 rows)
```
## FULL OUTER JOIN
```
mchinnappan=# SELECT * FROM sweet_grade
mchinnappan-#   FULL OUTER JOIN health_grade ON
mchinnappan-#        sweet_grade.name = health_grade.name;
  name  | score |   name    | score 
--------+-------+-----------+-------
 Plum   |     4 |           |      
 Mango  |     4 | Mango     |     5
 Apple  |     3 | Apple     |     5
 Peach  |     4 | Peach     |     4
 Banana |     4 | Banana    |     4
 Dates  |     5 | Dates     |     5
        |       | Jackfruit |     4
        |       | Pear      |     4
(8 rows)
```
## LEFT OUTER JOIN
```
mchinnappan=# SELECT * FROM sweet_grade
mchinnappan-#   LEFT OUTER JOIN health_grade ON
mchinnappan-#        sweet_grade.name = health_grade.name;
  name  | score |  name  | score 
--------+-------+--------+-------
 Plum   |     4 |        |      
 Mango  |     4 | Mango  |     5
 Apple  |     3 | Apple  |     5
 Peach  |     4 | Peach  |     4
 Banana |     4 | Banana |     4
 Dates  |     5 | Dates  |     5
(6 rows)
```

## RIGHT OUTER JOIN
```
               
mchinnappan=# SELECT * FROM sweet_grade
mchinnappan-#   RIGHT OUTER JOIN health_grade ON
mchinnappan-#        sweet_grade.name = health_grade.name;
  name  | score |   name    | score 
--------+-------+-----------+-------
 Mango  |     4 | Mango     |     5
 Apple  |     3 | Apple     |     5
 Peach  |     4 | Peach     |     4
 Banana |     4 | Banana    |     4
 Dates  |     5 | Dates     |     5
        |       | Jackfruit |     4
        |       | Pear      |     4
(7 rows)
```
