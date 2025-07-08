---
title: "Как выбрать первую строку в каждой группе, упорядоченную по некоторым колонкам"
date: 2018-01-31
---

Я просто покажу вам пример, как выбрать первую строку в каждой группе логинов, упорядоченную по колонкам IsActive и Created, надеюсь, вы поймете, как это работает.

Например, у меня есть таблица:

Id | Login | IsActive | Created  
1  | test1 |     1    | 2016-01-01  
2  | test1 |     0    | 2015-05-21  
3  | test2 |     0    | 2016-07-03  
4  | test2 |     0    | 2017-01-22

Я хочу выбрать только одну строку на логин, и этот логин должен быть активным, если нет строки, где какой-то логин активен, я хочу выбрать строку, которая была создана недавно. Итак, в моем случае это строки 1 и 4.

Для решения этой задачи я создал этот скрипт:

```sql
with cte as (
  select *,
  rank() over (partition by [Login] order by [Active] desc, Created desc) as [r]
  from [User]
)
SELECT * FROM cte where [r] = 1
```

С **rank() over** я отсортировал строки в нужном мне порядке и сохранил это в колонке \[r\]. Затем я выбрал только первую строку в каждой группе с этим:  
**SELECT \* FROM cte where \[r\] = 1**

Если вам нужно использовать это в join, просто поместите блок "with" сверху, как это:

```sql
with cte as (
  select *,
  rank() over (partition by [Login] order by [Active] desc, Created desc) as [r]
  from [User]
)
SELECT * FROM Employees emp
LEFT JOIN (SELECT * FROM cte where [r] = 1) u on emp.[Login]=u.[Login]
```
