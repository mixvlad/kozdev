---
title: "Разрешить аутентификацию по паролю SSH на удаленном сервере"
date: 2017-12-04
---

1\. Подключитесь к серверу и проверьте свойства ssh:

```bash
sudo nano /etc/ssh/sshd_config
```

```ini
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes
```

**PasswordAuthentication** должен быть установлен в **yes**.

2\. Теперь перезапустите службу ssh:

```bash
service ssh restart
```

3\. Попробуйте установить ssh соединение с аутентификацией по паролю:

```bash
ssh username@domain
```

Не забудьте заменить **username** и **domain** на ваши значения.

[Здесь](/create-admin-user-in-ubuntu-linux/) вы можете найти, как создать нового пользователя, если у вас его нет, для вашего ssh соединения.
