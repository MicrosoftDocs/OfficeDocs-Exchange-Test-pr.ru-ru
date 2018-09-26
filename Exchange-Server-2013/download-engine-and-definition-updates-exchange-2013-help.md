---
title: 'Загрузка обновлений подсистемы и определений: Exchange 2013 Help'
TOCTitle: Загрузка обновлений подсистемы и определений
ms:assetid: 8f2ca383-e463-4df0-aa5d-29afe2f81aaf
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ657471(v=EXCHG.150)
ms:contentKeyID: 50488620
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Загрузка обновлений подсистемы и определений

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-08_

Администраторы Microsoft Exchange Server 2013 могут вручную загрузить обновления ядра защиты от вредоносных программ и определения (сигнатуры). Настоятельно рекомендуется загрузить обновления ядра и определений на сервер Exchange Server до помещения его в рабочую среду.

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 5 минут

  - Для загрузки обновления компьютер должен быть способен подключиться к Интернету и устанавливать соединения через TCP-порт 80 (HTTP).

  - UNRESOLVED\_TOKEN\_VAL(PD\_Shell\_Only\_Procedure)

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Защита от вредоносных программ" в разделе [Разрешения для защиты от нежелательной почты и вредоносных программ](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование командной консоли для ручной загрузки обновления ядра и определений

Чтобы загрузить обновления ядра и определений, выполните следующую команду:
```powershell
    & $env:ExchangeInstallPath\Scripts\Update-MalwareFilteringServer.ps1 -Identity <FQDN of server>
```
В этом примере вручную загружается обновление ядра и определений на сервере с именем mailbox01.contoso.com:
```powershell
    & $env:ExchangeInstallPath\Scripts\Update-MalwareFilteringServer.ps1 -Identity mailbox01.contoso.com
```
При необходимости можно указать параметр –EngineUpdatePath, который позволяет загружать обновления из других источников, кроме выбранного по умолчанию http://forefrontdl.microsoft.com/server/scanengineupdate. Это может быть HTTP-адрес или UNC-путь; если указан последний, затем сетевой службе понадобится доступ к пути. В этом примере вручную загружается обновление ядра и определений из локального каталога на сервер с именем mailbox01.contoso.com:
```powershell
    & $env:ExchangeInstallPath\Scripts\Update-MalwareFilteringServer.ps1 -Identity mailbox01.contoso.com -EngineUpdatePath \\Server\sharename
```
## Как проверить, что все получилось?

Чтобы убедиться, что обновления успешно загружены, необходимые открыть окно просмотра событий и просмотреть журнал событий. Рекомендуется использовать фильтрацию событий FIPFS, как описано в следующей процедуре.

1.  В меню **Пуск** щелкните **Все программы** \> **Администрирование** \> **Просмотр событий**.

2.  В средстве просмотра событий разверните папку **Журналы Windows**, а затем щелкните узел **Приложение**.

3.  В меню **Действия** щелкните **Фильтровать текущий журнал**.

4.  В диалоговом окне **Фильтровать текущий журнал** в раскрывающемся списке **Источники событий** установите флажок **FIPFS**, а затем щелкните **ОК**.

Если обновления были загружены успешно, вы увидите код события 6033, который будет выглядеть следующим образом:

`MS Filtering Engine Update process performed a successful scan engine update.`

`Scan Engine: Microsoft`

`Update Path: http://forefrontdl.microsoft.com/server/scanengineupdate`

`Last Update time: ‎2012‎-‎08‎-‎16T13:22:17.000Z`

`Engine Version: 1.1.8601.0`

`Signature Version: 1.131.2169.0`

## Дополнительные сведения

[Настройка политик защиты от вредоносных программ](configure-anti-malware-policies-exchange-2013-help.md)

