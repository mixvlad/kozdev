---
title: "Настройка таймаута WebClient в PowerShell"
date: 2016-11-09
---

Если вы хотите настроить значение таймаута для метода downloadString класса WebClient в PowerShell, вам нужно расширить класс WebClient, потому что свойство Timeout не является публичным.

Итак, в следующем примере я наследовал новый класс ExtendedWebClient от класса WebClient. И я добавил публичное поле Timeout к новому классу. Затем я переопределил метод GetWebRequest, чтобы использовать поле Timeout.

```powershell
$Source = @"
using System.Net;

public class ExtendedWebClient : WebClient
{
public int Timeout;

protected override WebRequest GetWebRequest(System.Uri address)
{
WebRequest request = base.GetWebRequest(address);
if (request != null)
{
request.Timeout = Timeout;
}
return request;
}

public ExtendedWebClient()
{
Timeout = 600000; // Timeout value by default
}
}
"@;

Add-Type -TypeDefinition $Source -Language CSharp

$webClient = New-Object ExtendedWebClient;
$webClient.Timeout = 1800000; # Change timeout for webClient
$loadData = $webClient.downloadString('http://your_url')
```
