---
title: 'Экспорт и импорт тегов хранения: Exchange 2013 Help'
TOCTitle: Экспорт и импорт тегов хранения
ms:assetid: 18405ea2-7ccc-475e-bd84-8b040e17bf44
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ907307(v=EXCHG.150)
ms:contentKeyID: 51408006
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Экспорт и импорт тегов хранения

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2017-11-15_

Существует несколько сценариев, в которых может потребоваться экспортировать или импортировать теги хранения. Они перечислены далее.

  - Применение одинаковых политик хранения на всех серверах в организации Exchange с несколькими лесами.

  - Применение одинаковых политик хранения в условиях гибридного развертывания, при котором часть почтовых ящиков остается в локальной организации Exchange, а другая часть — в службе Exchange Online.

  - Применение политик хранения при использовании архивации на базе Exchange, в рамках которой для пользователей с локальными почтовыми ящиками Exchange 2010 и более поздних версий настроен облачный архив.

В этих сценариях помощник для управляемых папок может правильно обработать элемент с применяемым тегом хранения после того, как элемент или почтовый ящик будет перенесен в другую организацию.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.Caution(EXCHG.150).gif" title="Внимание!" alt="Внимание!" />Внимание!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Чтобы синхронизировать теги и политики хранения между двумя организациями, при каждом изменении тега или политики хранения в исходной организации необходимо выполнить эту процедуру для экспорта тегов и политик хранения из исходной организации и их импорта в целевую организацию.<br />
Для экспорта невозможно выбрать конкретные теги или политики хранения. Сценарий Export-RetentionTags.ps1 экспортирует все теги и политики хранения из организации.</td>
</tr>
</tbody>
</table>


Дополнительные задачи управления, связанные с управлением записями сообщений (MRM), см. в разделе [Процедуры управления записями сообщений](messaging-records-management-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 10 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Управление записями сообщений" в разделе [Политика обмена сообщениями и разрешения для соответствия требованиям](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Процедуры, описанные в этой статье, основаны на использовании следующих трех файлов в папке `%ExchangeInstallPath%Scripts` на вашем сервере Exchange:
    
      - Export-RetentionTags.ps1
    
      - Import-RetentionTags.ps1
    
      - MigrateRetentionTags.strings.psd1

  - Для экспорта или импорта невозможно выбрать конкретные теги или политики хранения. Сценарий Export-RetentionTags.ps1 экспортирует все теги и политики хранения из организации. Сценарий Import-RetentionTags.ps1 импортирует все теги и политики хранения в импортируемом XML-файле, заменяя все имеющиеся теги и политики хранения в организации Exchange.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>


## Шаг 1. Экспорт тегов хранения из локальной организации Exchange

1.  Чтобы изменить каталог на подкаталог **Сценарии**, расположенный по пути установки сервера Exchange, в командной консоли выполните указанную ниже команду Командная консоль Exchange.
    
        Cd $Env:ExchangeInstallPath\Scripts

2.  Для экспорта тегов хранения в XML-файл выполните сценарий Export-RetentionTags.ps1.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>При импорте или экспорте тегов и политик сохранения в Exchange Online необходимо подключить свой сеанс Windows PowerShell к Exchange Online. Подробнее: <a href="https://technet.microsoft.com/ru-ru/library/jj984289(v=exchg.150)">Подключение к Exchange Online с помощью удаленной оболочки PowerShell</a>.</td>
    </tr>
    </tbody>
    </table>
    
        .\Export-RetentionTags.ps1 "c:\docs\ExportedRetentionTags.xml"

## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно экспортировали теги и политики хранения, выполните следующие действия.

1.  Перейдите по пути, указанному в команде экспорта, и убедитесь, что XML-файл с заданным вами именем создан.

2.  При необходимости вы можете открыть XML-файл в текстовом редакторе, чтобы изучить его содержимое.

## Шаг 2. Импорт тегов хранения в организацию Exchange

1.  Чтобы изменить каталог на подкаталог **Сценарии**, расположенный по пути установки сервера Exchange, в командной консоли выполните указанную ниже команду Командная консоль Exchange.
    
        Cd $Env:ExchangeInstallPath\Scripts

2.  Для импорта тегов хранения из ранее экспортированного XML-файла выполните сценарий Import-RetentionTags.ps1.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>При импорте или экспорте тегов и политик сохранения в Exchange Online необходимо подключить свой сеанс Windows PowerShell к Exchange Online. Подробнее: <a href="https://technet.microsoft.com/ru-ru/library/jj984289(v=exchg.150)">Подключение к Exchange Online с помощью удаленной оболочки PowerShell</a>.</td>
    </tr>
    </tbody>
    </table>
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>При выполнении этого сценария для службы Exchange Online может потребоваться подтвердить запуск программного обеспечения, предоставленного ненадежным издателем. Убедитесь, что имя издателя отображается как <code>CN=Microsoft Corporation, OU=MOPR, O=Microsoft Corporation, L=Redmond, S=Washington, C=US</code>, а затем выберите <strong>R</strong>, чтобы выполнить сценарий один раз, или <strong>A</strong>, чтобы выполнять его всегда.</td>
    </tr>
    </tbody>
    </table>
    
        .\Import-RetentionTags.ps1 "c:\docs\ExportedRetentionTags.xml"

## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно импортировали теги и политики хранения, выполните следующие действия.

1.  В EAC перейдите к пункту **Управление соответствием** \> **Теги хранения** и проверьте, успешно ли импортированы теги хранения. Перейдите к пункту **Управление соответствием** \> **Теги хранения** и проверьте, успешно ли импортированы политики хранения.

2.  Используйте командлеты **Get-RetentionPolicy** и **Get-RetentionPolicyTag**, чтобы проверить создание тегов и политик хранения. Пример получения тегов и политик хранения см. в разделах [Get-RetentionPolicyTag](https://technet.microsoft.com/ru-ru/library/dd298009\(v=exchg.150\)) и [Get-RetentionPolicy](https://technet.microsoft.com/ru-ru/library/dd298086\(v=exchg.150\)).

