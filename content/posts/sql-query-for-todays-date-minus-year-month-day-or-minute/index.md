---
title: "SQL запрос для сегодняшней даты минус год, месяц, день или минута"
date: 2021-10-09
---

Для добавления или вычитания даты/времени вы можете использовать функцию MS SQL:

DATEADD(datepart, number, date)

Допустим, вам нужно добавить пять месяцев к текущей дате, используйте это:

```sql
SELECT * FROM YourTable
WHERE YourDate < DATEADD(month, 5, GETDATE())
```

Я использовал функцию GETDATE() для получения текущей даты и времени.

Если вам нужно вычесть некоторое время, просто добавьте минус ко второму параметру:

```sql
SELECT * FROM YourTable
WHERE YourDate < DATEADD(month, -5, GETDATE())
```

Список доступных аргументов для параметра datepart:

*   year
*   quarter
*   month
*   dayofyear
*   day
*   week
*   weekday
*   hour
*   minute
*   second
*   millisecond
*   microsecond
*   nanosecond

[Смотрите полную информацию о функции MS SQL DATEADD на сайте Microsoft](https://docs.microsoft.com/en-us/sql/t-sql/functions/dateadd-transact-sql)
