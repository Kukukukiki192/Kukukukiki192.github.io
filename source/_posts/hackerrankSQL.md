---
title: HackerRank-SQL
date: 2021-10-13 22:50:06
tags: Mysql
index_img: /img/hackerRank.png
banner_img: /img/MC_earth.jpg
---
[MySQL 函数](https://www.begtut.com/sql/sql-ref-mysql.html)

:green_circle: easy :yellow_circle: medium :red_circle: hard
## [1. Type of Triangle](https://www.hackerrank.com/challenges/what-type-of-triangle/problem?isFullScreen=true) :green_circle:
```sql
-- select 
--     case
--     when A=B and B=C then "Equilateral"
--     when A=B or B=C or A=C then "Isosceles" 
--     --(1 1 0 is not a triangle, next line should come befor this line)
--     when A+B<=C or A+C<=B or B+C<=A then "Not A Triangle"
--     else "Scalene"
--     end
-- from TRIANGLES

select 
    case 
    when A+B<=C or A+C<=B or B+C<=A then "Not A Triangle"
    when A=B and B=C then "Equilateral"
    when A=B or B=C or A=C then "Isosceles"           
    else "Scalene"
    end
from TRIANGLES

-- A+B>C -> A+B+C>2*C greatest(A,B,C):select max
select 
    case
    when greatest(A,B,C)*2>=(A+B+C) then "Not A Triangle" 
    when A=B and B=C then "Equilateral"
    when A=B or B=C or A=C then "Isosceles"
    else "Scalene"
    end
from TRIANGLES
```
## [2. Binary Tree Nodes](https://www.hackerrank.com/challenges/binary-search-tree-1/problem?isFullScreen=true) :yellow_circle:
```sql
select N,
    case
    when P is null then 'Root'
    when N in(select distinct P from BST) then 'Inner'
    else 'Leaf'
    end
from BST
order by N;

--
select N, if(P is null, 'Root', if(N in(select distinct P from BST), 'Inner', 'Leaf'))
from BST
order by N;
```

To be updated...