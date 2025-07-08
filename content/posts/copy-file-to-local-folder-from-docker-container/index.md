---
title: "Скопировать файл в локальную папку из docker контейнера"
date: 2022-08-12
---

Проверьте containerId, выполнив эту команду:

```powershell
sudo docker ps
```

Чтобы скопировать файл из контейнера на локальный компьютер, используйте следующую команду:

```powershell
docker cp :/file_path_inside_container /local_path
```

Вы можете проверить полный путь к файлу внутри контейнера с помощью этой команды:

```powershell
readlink -f file.ext
```
