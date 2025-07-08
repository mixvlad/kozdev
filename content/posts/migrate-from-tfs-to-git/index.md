---
title: "Миграция с TFS на Git"
date: 2017-05-17
---

Прежде всего скачайте git-tfs отсюда:

[http://git-tfs.com](http://git-tfs.com)

Правый клик на Мой компьютер -> Свойства -> Дополнительные параметры системы -> Переменные среды -> Системные переменные -> Path

Добавьте **;C:\\TfsMigration\\GitTfs-0.25.1** в конец переменной Path.

Откройте командную строку от имени администратора и выполните следующие команды, не забудьте изменить команды с вашими переменными:

```bash
git tfs clone http://myserver:8080/tfs/DefaultCollection $/PIK.BOP/Trunk . --branches=all
```

```bash
git remote add origin http://[email protected]/apps/autobop-backend.git
```

Я использую **\-c http.sslVerify=false** потому что у меня проблемы с сертификатом сервера.

```bash
git -c http.sslVerify=false push --all origin
```

Если ваш сервер настроен правильно, я рекомендую использовать предыдущую команду без **\-c http.sslVerify=false**:

```bash
git push --all origin
```

Полное описание о миграции с TFS на Git вы можете найти здесь:

[https://github.com/git-tfs/git-tfs/blob/master/doc/usecases/migrate\_tfs\_to\_git.md](https://github.com/git-tfs/git-tfs/blob/master/doc/usecases/migrate_tfs_to_git.md)
