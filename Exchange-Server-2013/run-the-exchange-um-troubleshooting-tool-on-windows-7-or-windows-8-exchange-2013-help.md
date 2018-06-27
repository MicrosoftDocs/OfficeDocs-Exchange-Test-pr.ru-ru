---
title: 'Запуск средства устранения неполадок единой системы обмена сообщениями Exchange в операционной системе Windows 7 или Windows 8: Exchange 2013 Help'
TOCTitle: Запуск средства устранения неполадок единой системы обмена сообщениями Exchange в операционной системе Windows 7 или Windows 8
ms:assetid: 98d6869d-ee4a-4088-849d-ef75b0f5d932
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff851872(v=EXCHG.150)
ms:contentKeyID: 56271234
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Запуск средства устранения неполадок единой системы обмена сообщениями Exchange в операционной системе Windows 7 или Windows 8

 

_**Применимо к:**Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2016-12-09_

Средство устранения неполадок единой системы обмена сообщениями Microsoft Exchange 2010 — командлет командной консоли Exchange, **Test-ExchangeUMCallFlow**. С помощью этого командлета вы можете диагностировать ошибки конфигурации, связанные со сценариями ответа на вызовы, и проверки правильности работы голосовой почты при локальном и гибридном развертывании единой системы обмена сообщениями в Microsoft Exchange Server 2010 с пакетом обновления 1 (SP1) или более поздней версии. Вы также можете использовать этот командлет при развертывании Microsoft Lync Server 2010 или более поздней версии для Microsoft Office, а также при развертывании единой системы обмена сообщениями с использованием VoIP-шлюзов, IP-УАТС или пограничных контроллеров сеансов (SBC).

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения: 3 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье записи "Сервер единой системы обмена сообщениями" или "Службы единой системы обмена сообщениями" в статье [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Убедитесь, что ваша организация Exchange 2010 или Exchange 2013 соответствует следующим требованиям:
    
      - Создана абонентская группа единой системы обмена сообщениями. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).
    
      - Создана политика почтовых ящиков единой системы обмена сообщениями. Дополнительные сведения см. в разделе [Создание политики почтовых ящиков единой системы обмена сообщениями](create-a-um-mailbox-policy-exchange-2013-help.md).
    
      - Создан шлюз IP единой системы обмена сообщениями. Дополнительные сведения см. в разделе [Создание шлюза IP единой системы обмена сообщениями](create-a-um-ip-gateway-exchange-2013-help.md).
    
      - Сервер единой системы обмена СООБЩЕНИЯМИ Exchange 2010 добавлена для абонентской группы единой системы обмена СООБЩЕНИЯМИ. При использовании Exchange 2013 с Lync Server добавьте всех серверах клиентского доступа и почтовых ящиков абонентских групп SIP URI. Подробное описание процедуры в разделе [Добавление сервера единой системы обмена СООБЩЕНИЯМИ для Dial Plan,](https://go.microsoft.com/fwlink/p/?linkid=313051) или [Добавьте серверы клиентского доступа и почтовых ящиков для абонентской группы SIP URI](add-mailbox-and-client-access-servers-to-a-sip-uri-dial-plan-exchange-2013-help.md).

  - Если вы запустите средство устранения неполадок единой системы обмена сообщениями на локальном сервере этой системы с Exchange 2010 с пакетом обновления 1 (SP1) или более поздних версий или на сервере почтовых ящиков Exchange 2013, может не потребоваться устанавливать все обязательные компоненты, указанные ниже. Они могут быть уже установлены вместе с ролью сервера единой системы обмена сообщениями. Тем не менее, при установке средства устранения неполадок единой системы обмена сообщениями на 64-разрядном компьютере, который не является сервером с запущенной ролью сервера единой системы обмена сообщениями, необходимо установить следующие компоненты.
    
      - Microsoft .NET Framework 3.5 пакетом обновления 1 (SP1). В разделе [Microsoft .NET Framework 3.5 с пакетом обновления 1](https://go.microsoft.com/fwlink/p/?linkid=152380).
    
      - Если средство будет выполняться в Windows Vista или Windows Server 2008 компьютер, посетите страницу [обновление для семейства Microsoft .NET Framework 3.5 для x64, Windows Vista и Windows Server 2008 x64](https://go.microsoft.com/fwlink/p/?linkid=178998).
    
      - Служба удаленного управления Windows (WinRM) 2.0 и Windows PowerShell V2 (Windows6.0-KB968930.msu). См. статью 968930 базы знаний Майкрософт [Основной пакет Windows Management Framework (Windows PowerShell 2.0 и WinRM 2.0)](http://go.microsoft.com/fwlink/?linkid=3052%26kbid=968930).
    
      - Microsoft Unified Communications Managed API 2.0 среда выполнения (UcmaRuntimeWebDownloadX64.msi). В разделе [API 2.0, среда выполнения (64-разрядная версия) под управлением объединенных коммуникаций](https://go.microsoft.com/fwlink/p/?linkid=198175).

  - Загрузите и установите средство устранения неполадок единой системы обмена сообщениями.
    
      - [Единая система обмена сообщениями, средства устранения неполадок](https://go.microsoft.com/fwlink/p/?linkid=182625) загрузите из центра загрузки Майкрософт.
    
      - Установите это средство. Дополнительные сведения см. в разделе [Установка средства устранения неполадок единой системы обмена сообщениями Exchange](install-the-exchange-um-troubleshooting-tool-exchange-2013-help.md).
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Если будет использоваться единой системы обмена СООБЩЕНИЯМИ средство устранения неполадок в режиме <code>SIPClient</code> , существует несколько других Office Communications Server 2007 R2 или Lync Server Майкрософт требования и предварительные условия, которые должны быть выполнены. Дополнительные сведения можно <a href="https://go.microsoft.com/fwlink/p/?linkid=311961">Контрольный список: развертывание Office Communications Server 2007 R2 и единой системы обмена сообщениями Exchange 2010</a>.</td>
        </tr>
        </tbody>
        </table>


  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..</td>
</tr>
</tbody>
</table>


## Запуск средства устранения неполадок единой системы обмена сообщениями в Windows Vista, Windows 7 или Windows 8

1.  Выберите **Пуск** \> **Все программы** \> **Стандартные** \> **Windows PowerShell**.

2.  Нажмите правой кнопкой мыши **Windows PowerShell** и во всплывающем меню выберите пункт **Запуск от имени администратора**.

3.  В командной строке Windows PowerShell перейдите к папке, в которую установлено средство устранения неполадок единой системы обмена сообщениями, и запустите следующую команду.
    
        C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -psconsolefile .\Microsoft.Exchange.UM.TroubleshootingToolsnapin.psc1 -noexit -command ". '.\Microsoft.Exchange.UM.TroubleshootingTool.ps1' "

4.  При запуске средства устранения неполадок единой системы обмена сообщениями в Windows Vista, Windows 7 или Windows 8 в командной строке Windows PowerShell выполните следующую команду:
    
        Set-ExecutionPolicy RemoteSigned

5.  в меню **Пуск** откройте **Средство устранения неполадок единой системы обмена сообщениями Microsoft Exchange 2010**.

6.  В окне **Средство устранения неполадок единой системы обмена сообщениями Microsoft Exchange 2010** в командной строке введите следующую команду и нажмите клавишу ВВОД.
    
        $cred=Get-Credential

7.  В окне **Запрос учетных данных Windows PowerShell** введите домен\\имя\_пользователя и пароль, а затем нажмите кнопку **ОК**.

8.  В окне **Средство устранения неполадок единой системы обмена сообщениями Microsoft Exchange 2010** укажите обязательные параметры командлета для проверки потока вызовов. Например:
    
        Test-ExchangeUMCallFlow -Mode SIPClient -CallingParty tonysmith@contoso.com - CalledParty jamiestark@contoso.com NextHop ocsfe.contoso.com -Credential $cred

