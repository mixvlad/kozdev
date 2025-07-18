---
title: "MS SQL вставка в середину и сброс автоинкремента"
date: 2022-04-28
---

В случае, если вам нужно вставить что-то в середину и нужно установить автоинкрементную колонку в некоторые конкретные значения, вы можете сделать следующее:

```sql
Set Identity_Insert [TableName] On -- Включить identity insert для вашей Таблицы
-----------------------------------
Insert TableName (pkCol, [OtherColumns])
Values(pkValue, [OtherValues])
-----------------------------------
Set Identity_Insert [TableName] Off -- Выключить identity insert для вашей Таблицы
```

В случае, если вам нужно переустановить автоинкремент в MS SQL, используйте это:

```sql
DBCC CHECKIDENT ([TableName], RESEED, 0) -- вы переустановите PK [TableName] чтобы начать с 1
```

Если вам нужно начать не с 0, а с другого числа, вы можете изменить последний параметр, как это:

```sql
DBCC CHECKIDENT ([TableName], RESEED, 123) -- PK будет начинаться с 124, измените число при необходимости
```
