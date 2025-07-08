---
title: "Добавить настройки прокси в приложения IIS с помощью web.config"
date: 2020-03-27
---

Чтобы установить настройки прокси для вашего приложения IIS, просто добавьте следующий блок в ваш файл web.config:

```yaml
<system.net>
    <defaultProxy>
      <proxy proxyaddress="http://192.168.0.1:8080" bypassonlocal="true" />
    </defaultProxy>
</system.net>
```

Поместите настройки вашего прокси-сервера в поле "proxyaddress".
