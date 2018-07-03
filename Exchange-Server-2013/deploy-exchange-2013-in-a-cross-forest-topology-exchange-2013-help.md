---
title: 'Развертывание Exchange 2013 в топологии с несколькими лесами: Exchange 2013 Help'
TOCTitle: Развертывание Exchange 2013 в топологии с несколькими лесами
ms:assetid: 65be650f-d435-4f60-9ff0-5cb88a726abb
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa998597(v=EXCHG.150)
ms:contentKeyID: 51408034
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Развертывание Exchange 2013 в топологии с несколькими лесами

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

В этом разделе рассказывается, как выполнить развертывание Exchange 2013 в топологии перекрестного леса с помощью Microsoft Forefront Identity Manager 2010 R2 с пакетом обновления 1 (SP1). Чтобы развернуть систему Exchange 2013 в топологии перекрестного леса, необходимо предварительно установить систему Exchange 2013 в каждом лесу, а затем соединить леса, чтобы пользователи могли видеть адреса и данные о доступности в лесах.

На следующем рисунке показана синхронизация пользователя между двумя лесами Exchange 2013.

**Пример синхронизации между лесами в Exchange 2013**

![Пример топологии Exchange 2010 с несколькими лесами](images/Aa998597.df0ba5dd-cb96-4542-98bd-2a425defe317(EXCHG.150).gif "Пример топологии Exchange 2010 с несколькими лесами")

В этом разделе *не* рассказывается о том, как выполнить развертывание Exchange 2013 в топологии выделенного леса (или леса ресурсов) Exchange. Дополнительные сведения о развертывании системы Exchange 2013 в топологии леса ресурсов см. в разделе [Развертывание Exchange 2013 в топологии леса ресурсов Exchange](deploy-exchange-2013-in-an-exchange-resource-forest-topology-exchange-2013-help.md).

## Что нужно знать перед началом работы

Чтобы выполнить следующую процедуру в системе Exchange 2013, убедитесь в следующем.

  - Система DNS для разрешения имен в лесах организации настроена правильно. Чтобы проверить, правильно ли настроена служба DNS, используйте средство проверки связи для проверки соединения с каждым лесом из других лесов организации и с сервера, на котором будет запущен агент синхронизации глобального списка адресов.

  - Агент управления GALSync взаимодействует с лесом Exchange 2013 с помощью окончательной первоначальной версии (RTM) Windows PowerShell V2.0. Убедитесь, что Windows PowerShell версии 1.0 не установлена на этом компьютере. Для этого откройте панель управления и выберите "Программы и компоненты".

  - Убедитесь, что удаленное управление Windows не установлено с помощью Центра обновления Windows.

  - Установите Windows PowerShell и удаленное управление Windows. Дополнительные сведения см. в статье 968930 базы знаний Майкрософт [Основной пакет Windows Management Framework (Windows PowerShell 2.0 и WinRM 2.0)](http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=968930).

  - Загрузите Forefront Identity Manager 2010 R2 с пакетом обновления 1 (SP1). См. раздел [Скачать Microsoft Forefront Identity Manager 2010 R2 с пакетом обновления 1 (SP1)](https://go.microsoft.com/fwlink/p/?linkid=279868).

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


## Развертывание Exchange 2013 в топологии перекрестного леса с помощью Forefront Identity Manager 2010 R2 с пакетом обновления 1 (SP1)

1.  Установите систему Exchange 2013 отдельно в каждом лесу. Чтобы установить Exchange 2013, выполните те же шаги, которые выполняются при установке сервера Exchange 2013 в топологии с одним лесом. Подробное описание выполняемых шагов см. в одном из следующих разделов:
    
      - [Развертывание новой установки Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md)
    
      - [Установка Exchange 2013 с помощью мастера установки](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md)
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>В этом разделе предполагается, что топология Exchange 2007 или Exchange 2010 отсутствует. Если существует топология Exchange и ее требуется обновить, то сведения о том, как это сделать, см. в разделе <a href="upgrade-from-exchange-2010-to-exchange-2013-exchange-2013-help.md">Обновление с Exchange 2010 до Exchange 2013</a> или в разделе <a href="upgrade-from-exchange-2007-to-exchange-2013-exchange-2013-help.md">Обновление с Exchange 2007 до Exchange 2013</a>.</td>
        </tr>
        </tbody>
        </table>


2.  В каждом лесу с помощью средства "Пользователи и компьютеры Active Directory" создайте контейнер, в котором Forefront Identity Manager 2010 R2 с пакетом обновления 1 (SP1) создаст контакты для каждого почтового ящика из другого леса. Рекомендуется назвать этот контейнер **FromFIM**. Чтобы создать контейнер, выберите домен, в котором будет создан контейнер, щелкните правой кнопкой мыши домен, выберите команду **Создать** \> **Подразделение**. В окне **Создание объекта — Подразделение** введите **FromFIM** и нажмите кнопку **OK**.

3.  С помощью Forefront Identify Manager создайте агент управления GALSync для каждого леса. Это позволит синхронизировать пользователей в каждом лесу и создать общий глобальный список адресов (GAL). Подробные пошаговые инструкции см. в следующих разделах.
    
      - [Настройка синхронизации глобального списка адресов (GAL) с помощью Forefront Identity Manager (FIM) 2010](https://go.microsoft.com/fwlink/p/?linkid=279869)
    
      - [Работа с агентами управления](https://go.microsoft.com/fwlink/p/?linkid=279870)
    
      - [Стратегия документации Forefront Identity Manager 2010 R2](https://go.microsoft.com/fwlink/p/?linkid=279871)
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Хотя в этих статьях рассказывается об Exchange 2010, Forefront Identity Manager 2010 R2 с пакетом обновления 1 (SP1) также поддерживает Exchange 2013. Убедитесь, что параметр <strong>Расширения</strong> в Forefront Identity Manager 2010 R2 с пакетом обновления 1 (SP1) настроен для Exchange 2013.</td>
    </tr>
    </tbody>
    </table>
    
    1.  На странице **Настройка расширений** в разделе **Настройка отображаемых имен разделов** рядом с пунктом **Подготовить для** выберите **Exchange 2013**. Отобразится поле **Exchange 2013 RPS URI**. Введите универсальный код ресурса (URI) сервера клиентского доступа Exchange 2013, чтобы убедиться, что подключение к удаленной оболочке PowerShell работает. Значение поля **Универсальный код ресурса (URI) Exchange 2013 RPS** должно иметь следующий формат: http://Имя\_FQDN\_сервера\_клиентского\_доступа/Powershell. Нажмите кнопку **ОК**.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Убедитесь, что учетные данные администратора, используемые для подключения к лесу Exchange 2013, позволяют также устанавливать подключения Remote PowerShell к этому лесу.<br />
        На следующем рисунке показано, как выбрать способ подготовки для системы Exchange 2013.</td>
        </tr>
        </tbody>
        </table>
        
        **Подготовка агента управления GalSync для системы Exchange 2013**
        
        ![Подготовка агента управления в Exchange 2010](images/Aa998597.8f403cda-e5e4-4edf-887f-c1ed46cee3f5(EXCHG.150).gif "Подготовка агента управления в Exchange 2010")  

4.  Создайте в каждом из лесов соединитель отправки SMTP. Дополнительные сведения см. в разделе [Настройка соединителя отправки между лесами](configure-a-cross-forest-send-connector-exchange-2013-help.md).

5.  В каждом лесе включите службу доступности, чтобы пользователи в каждом лесе могли просматривать данные занятости о пользователях в другом лесе. Подробнее см. в разделе [Служба доступности в Exchange 2013](availability-service-in-exchange-2013-exchange-2013-help.md).

6.  Если необходимо ретранслировать почту через какой-либо лес в организации, следует настроить домен в этом лесу в качестве доверенного. Дополнительные сведения см. в разделе [Настройка Exchange для приема почты для нескольких уполномоченных доменов](configure-exchange-to-accept-mail-for-multiple-authoritative-domains-exchange-2013-help.md).

