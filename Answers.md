1.) Find the names of all students who are friends with someone named Gabriel.
```sql
    select h1.name
    from Highschooler h1
    where ID IN (
        select ID1
        from Friend, Highschooler h2
        where 
    )
```

2.) Find all students who do not appear in the Likes table (as a student who likes or is liked) and return their names and grades.
```sql
    select h.name, h.grade
    from Highschooler h
    where h.ID NOT IN(
        select h2.ID
        from Likes, Highschooler h2
        where ID1 <> h.ID AND ID2 <> h.ID);
```

3.) (*) Find the name and grade of all students who are liked by more than one other student.
```sql
    select
    from 
    where 
```

4.) For every student who likes someone 2 or more grades younger than themselves, return that student's name and grade, and the name and grade of the student they like. Note that your conditions in the where clause can include any arithmetic expressions, e.g. (a-b > 10) AND (c < d2).
```sql
    select
    from 
    where 
```