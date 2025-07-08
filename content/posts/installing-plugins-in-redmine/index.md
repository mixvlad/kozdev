---
title: "Полезные плагины Redmine и как установить их в Bitnami Redmine"
date: 2020-01-23
---

Список плагинов:

[http://www.redmine.org/plugins/boolean\_query](http://www.redmine.org/plugins/boolean_query)

Чтобы установить плагины, выполните следующие команды в папке htdocs redmine (для меня это "/opt/bitnami/apps/redmine/htdocs"):

```bash
bundle install
```

```bash
bundle exec rake redmine:plugins:migrate RAILS_ENV=production
```

И перезапустите apache. Я использую следующую команду для этого:

```bash
/opt/redmine-3.3.2-2/ctlscript.sh restart apache
```
