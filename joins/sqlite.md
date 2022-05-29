# Explaining JOINS using sqlite
```
sqlite> create table sweet_grade (name varchar(32), score int);

sqlite> insert into sweet_grade (name, score) values ('Plum', 4), ('Mango', 4), ('Apple',3), ('Peach', 4), ('Banana', 4), ('Dates', 5);

sqlite> select * from sweet_grade ;
Plum|4
Mango|4
Apple|3
Peach|4
Banana|4
Dates|5

sqlite> create table health_grade (name varchar(32), score int);
sqlite> insert into health_grade (name, score) values ('Mango', 5), ('Apple',5), ('Peach', 4), ('Banana', 4), ('Dates', 5), ('Jackfruit',4), ('Pear', 4);


sqlite> select * from health_grade ;
Mango|5
Apple|5
Peach|4
Banana|4
Dates|5
Jackfruit|4
Pear|4


```
## Inner Join

```sql
SELECT * FROM sweet_grade 
  INNER JOIN health_grade ON 
       sweet_grade.name = health_grade.name;

```

```
Mango|4|Mango|5
Apple|3|Apple|5
Peach|4|Peach|4
Banana|4|Banana|4
Dates|5|Dates|5
```

## Full Outer Join

```sql
SELECT * FROM sweet_grade 
  FULL OUTER JOIN health_grade ON 
       sweet_grade.name = health_grade.name;

```

```
Error: RIGHT and FULL OUTER JOINs are not currently supported
```

## Left Outer Join

```sql
SELECT * FROM sweet_grade 
  LEFT OUTER JOIN health_grade ON 
       sweet_grade.name = health_grade.name;

```
```
Plum|4||
Mango|4|Mango|5
Apple|3|Apple|5
Peach|4|Peach|4
Banana|4|Banana|4
Dates|5|Dates|5
```


## Right Outer Join

```sql
SELECT * FROM sweet_grade 
  RIGHT OUTER JOIN health_grade ON 
       sweet_grade.name = health_grade.name;

```

```
Error: RIGHT and FULL OUTER JOINs are not currently supported

```



