1.) Find the names of all students who are friends with someone named Gabriel.
```sql
select h.name
from Highschooler h, Friend f
where f.ID1 = h.ID
    AND f.ID2 IN(
    select ID
    from Highschooler
    where name = "Gabriel");
```

2.) Find all students who do not appear in the Likes table (as a student who likes or is liked) and return their names and grades.
```sql
select h.name, h.grade
from Highschooler h
where h.ID NOT IN(
    select h.ID
    from Highschooler h, Likes l
    where l.ID1 = h.ID OR l.ID2 = h.ID);
```

3.) (*) Find the name and grade of all students who are liked by more than one other student.
```sql
select name, grade
from Highschooler
where ID IN (
    select ID2
    from Likes
    group by ID2 having count(*) > 1);
```

4.) For every student who likes someone 2 or more grades younger than themselves, return that student's name and grade, and the name and grade of the student they like. Note that your conditions in the where clause can include any arithmetic expressions, e.g. (a-b > 10) AND (c < d2).
```sql
select h1.name, h1.grade, h2.name, h2.grade
from Highschooler h1, Highschooler h2, Likes l
where h1.ID = l.ID1 
    AND h2.ID = l.ID2
    AND h1.grade - h2.grade >= 2;
    
```