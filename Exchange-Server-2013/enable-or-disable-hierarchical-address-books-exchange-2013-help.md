---
title: 'Включение и отключение иерархических адресных книг: Exchange 2013 Help'
TOCTitle: Включение и отключение иерархических адресных книг
ms:assetid: b4c3a175-ce5e-4bfb-a4a0-92d25f3644b3
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff607473(v=EXCHG.150)
ms:contentKeyID: 50488889
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Включение и отключение иерархических адресных книг

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Вы можете настроить иерархическую адресную книгу, которая доступна для пользователей в Microsoft Outlook 2010 и более поздних версий. С помощью иерархической адресной книги пользователи могут искать получателей в своей организации Exchange, используя организационную иерархию на основе структуры старшинства или управления. Для получения дополнительных сведений о иерархических адресных книгах см. раздел [Иерархические адресные книги](hierarchical-address-books-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения: 1 час.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Группы рассылки" в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

  - Невозможно использовать Центр администрирования Exchange (EAC) для выполнения этой процедуры. Необходимо использовать командную консоль.

  - Прежде чем начать, ознакомьтесь с разделом [Иерархические адресные книги](hierarchical-address-books-exchange-2013-help.md). Следует определить, подходит ли иерархическая адресная книга для организации Exchange.

  - Определите настройку подразделений, групп, пользователей и контактов в организации Exchange.

  - Определите в следующей таблице командлеты и связанные параметры, которые необходимы для настройки иерархической адресной книги.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Командлет</th>
    <th>Параметр</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><a href="https://technet.microsoft.com/ru-ru/library/aa997443(v=exchg.150)">Set-OrganizationConfig</a></p></td>
    <td><p><em>HierarchicalAddressBookRoot</em></p></td>
    </tr>
    <tr class="even">
    <td><p><a href="https://technet.microsoft.com/ru-ru/library/bb123770(v=exchg.150)">Set-Group</a></p></td>
    <td><p><em>IsHierarchicalGroup</em></p>
    <p><em>SeniorityIndex</em></p>
    <p><em>PhoneticDisplayName</em></p></td>
    </tr>
    <tr class="odd">
    <td><p><a href="https://technet.microsoft.com/ru-ru/library/aa998221(v=exchg.150)">Set-User</a></p></td>
    <td><p><em>SeniorityIndex</em></p>
    <p><em>PhoneticDisplayName</em></p></td>
    </tr>
    <tr class="even">
    <td><p><a href="https://technet.microsoft.com/ru-ru/library/bb124535(v=exchg.150)">Set-Contact</a></p></td>
    <td><p><em>SeniorityIndex</em></p>
    <p><em>PhoneticDisplayName</em></p></td>
    </tr>
    </tbody>
    </table>


  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Использование командной консоли для включения иерархической адресной книги

> [!NOTE]  
> Центр администрирования Exchange нельзя использовать для включения иерархической адресной книги, но после того, как книга включена, с помощью Центра администрирования Exchange можно управлять членством в группах организационной иерархии.


Для этого примера в иерархической книге будет создано подразделение HAB. Домен организации называется Contoso-dom, а организация верхнего уровня иерархии будет называться Contoso,Ltd (*корневая организация*). Подчиненные группы с названиями Corporate Office, Product Support Organization и Sales & Marketing Organization будут созданы в узле Contoso,Ltd в качестве подчиненных организаций. Кроме того, в разделе Corporate Office будут созданы группы Human Resources, Accounting Group и Administration Group.

Дополнительные сведения о создании групп рассылок см. в разделе [Создание групп рассылки и управление ими](create-and-manage-distribution-groups-exchange-2013-help.md).

1.  Создайте подразделение HAB в организации Contoso. Для этого можно использовать окно Active Directory "Пользователи и компьютеры" или ввести следующую команду в командной строке.
    
    > [!NOTE]  
    > Кроме того, можно использовать существующее подразделение в лесу Exchange.
    
        dsadd ou "OU=HAB,DC=Contoso-dom,DC=Contoso,DC=com"
    
    > [!NOTE]  
    > Дополнительные сведения см. в разделе <a href="https://go.microsoft.com/fwlink/p/?linkid=198986">Создание нового подразделения</a>.


2.  Создайте корневую группу рассылки Contoso,Ltd для иерархической адресной книги.
    
    > [!NOTE]  
    > В этом примере описывается использование командной строки. Для создания группы рассылки можно также использовать Центр администрирования Exchange. Дополнительные сведения см. в разделе <a href="create-and-manage-distribution-groups-exchange-2013-help.md">Создание групп рассылки и управление ими</a>.
    
        New-DistributionGroup -Name "Contoso,Ltd" -DisplayName "Contoso,Ltd" -Alias "ContosoRoot" -OrganizationalUnit "Contoso-dom.Contoso.com/HAB" -SamAccountName "ContosoRoot" -Type "Distribution"

3.  Укажите Contoso,Ltd в качестве корневой организации для иерархической адресной книги.
    
        Set-OrganizationConfig -HierarchicalAddressBookRoot "Contoso,Ltd"

4.  Создайте группы рассылки для других уровней в HAB. Для этого примера необходимо создать следующие группы: Corporate Office, Product Support Organization, Sales & Marketing Organization, Human Resources, Accounting Group и Administration Group. В этом примере создается группа рассылки Corporate Office.
    
    > [!NOTE]  
    > В этом примере описывается использование командной строки. Для создания групп рассылки можно также использовать Центр администрирования Exchange. Дополнительные сведения см. в разделе <a href="create-and-manage-distribution-groups-exchange-2013-help.md">Создание групп рассылки и управление ими</a>.
    
        New-DistributionGroup -Name "Corporate Office" -DisplayName "Corporate Office" -Alias "CorporateOffice" -OrganizationalUnit "Contoso-dom.Contoso.com/HAB" -SamAccountName "CorporateOffice" -Type "Distribution"

5.  Назначьте группы в качестве членов HAB. Например, следующие группы следует указать в качестве иерархических: Contoso,Ltd, Corporate Office, Product Support Organization, Sales & Marketing Organization, Human Resources, Accounting Group и Administration Group. В следующем примере группа рассылки Contoso,Ltd указывается в качестве члена HAB.
    
        Set-Group -Identity "Contoso,Ltd" -IsHierarchicalGroup $true

6.  Добавьте подчиненные группы в качестве членов корневой организации. Например, группы рассылки Corporate Office, Product Support Organization и Sales & Marketing Organization добавляются в качестве членов корневой организации Contoso,Ltd в иерархической адресной книге. В следующем примере группа рассылки Corporate Office добавляется в качестве члена корневой группы рассылки Contoso,Ltd.
    
    > [!NOTE]  
    > В этом примере используется псевдоним групп рассылки.
    
        Add-DistributionGroupMember -Identity "ContosoRoot" -Member "CorporateOffice"

7.  Добавьте все подчиненные группы рассылки группы Corporate Office в качестве участников. Например, группы рассылки Human Resources, Accounting Group и Administration Group добавляются в качестве участников группы рассылки Corporate Office. В следующем примере группа рассылки Human Resources добавляется в качестве члена группы рассылки Corporate Office.
    
    > [!NOTE]  
    > В следующем примере используется псевдоним групп рассылки, а также предполагается, что псевдоним группы рассылки Human Resources имеет значение HumanResources.
    
        Add-DistributionGroupMember -Identity "CorporateOffice" -Member "HumanResources"

8.  Добавление пользователей в группы иерархической адресной книги. В этом примере пользователь David Hamilton (SMTP-адрес: DHamilton@contoso.com) является существующим пользователем подразделения Contoso-dom.Contoso.com/Users. Этот пользователь будет добавлен в группу Corporate Office. Повторите этот шаг для добавления других пользователей в группы иерархической адресной книги.
    
        Add-DistributionGroupMember -Identity "CorporateOffice" -Member "DHamilton"

9.  Установите параметр *SeniorityIndex* для групп иерархической адресной книги. В этом примере группа Corporate Office содержит три дочерних группы: Human Resources, Accounting Group и Administration Group. Вместо перечисления групп в обратном алфавитном порядке (по умолчанию) будет выбрана сортировка Human Resources (*SeniorityIndex* = 100), Accounting Group (*SeniorityIndex* = 50) и Administration Group (*SeniorityIndex* = 25). В этом примере параметр *SeniorityIndex* для группы Human Resources будет установлен равным 100.
    
        Set-Group -Identity "Human Resources" -SeniorityIndex 100
    
    > [!NOTE]  
    > Параметр <em>SeniorityIndex</em> является числовым значением и используется для сортировки групп или пользователей иерархической адресной книги в порядке убывания. Если параметр <em>SeniorityIndex</em> не установлен или равен у двух и более пользователей, то при сортировке в иерархической адресной книге используется значение параметра <em>PhoneticDisplayName</em>. В этом случае пользователи перечисляются в прямом алфавитном порядке. Если значение <em>PhoneticDisplayName</em> не установлено, то порядок сортировки иерархической адресной книги устанавливается на значение параметра <em>DisplayName</em> по умолчанию, а пользователи перечисляются в прямом алфавитном порядке.


10. Устанавливает параметр *SeniorityIndex* для пользователей в группах иерархической адресной книги. В этом примере группа Corporate Office содержит трех пользователей: Amy Alberts, David Hamilton, and Rajesh M. Patel. Вместо перечисления групп в обратном алфавитном порядке (по умолчанию) будет выбрана сортировка David Hamilton (*SeniorityIndex* = 100), Rajesh M. Patel (*SeniorityIndex* = 50) и Amy Alberts (*SeniorityIndex* = 25). В этом примере параметр *SeniorityIndex* для пользователя David Hamilton будет установлен равным 100.
    
        Set-User -Identity "DHamilton@contoso.com" -SeniorityIndex 100

После завершения указанных действий иерархическая адресная книга будет отображена в Outlook. Чтобы просмотреть иерархическую адресную книгу, откройте Outlook и выберите пункт **Адресная книга**. Иерархическая адресная книга отображается на вкладке **Организация**. Пример вкладки показан на следующем рисунке.

**Пример иерархической адресной книги для Contoso, Ltd**

![Диалоговое окно "Иерархическая адресная книга"](images/Ff629379.d8cc782f-61cd-44c4-9c74-432ebea0c3db(EXCHG.150).gif "Диалоговое окно \"Иерархическая адресная книга\"")

После создания иерархической адресной книги можно использовать Центр администрирования Exchange для управления членством в группах организационной иерархии. Для изменения параметра *SeniorityIndex* для новых групп или пользователей следует использовать командную строку.

Подробные сведения о синтаксисе и параметрах см. в следующих разделах:

  - [New-DistributionGroup](https://technet.microsoft.com/ru-ru/library/aa998856\(v=exchg.150\))

  - [Set-OrganizationConfig](https://technet.microsoft.com/ru-ru/library/aa997443\(v=exchg.150\))

  - [Set-Group](https://technet.microsoft.com/ru-ru/library/bb123770\(v=exchg.150\))

  - [Add-DistributionGroupMember](https://technet.microsoft.com/ru-ru/library/bb124340\(v=exchg.150\))

  - [Set-User](https://technet.microsoft.com/ru-ru/library/aa998221\(v=exchg.150\))

## Использование командной строки для отключения иерархической адресной книги

В этом примере отключается корневая организация, используемая для иерархической адресной книги.

    Set-OrganizationConfig -HierarchicalAddressBookRoot $null

> [!NOTE]  
> Эта команда не удаляет корневую организацию и подчиненные группы, используемые в структуре иерархической адресной книги, и не сбрасывает значения <em>SeniorityIndex</em> для групп или пользователей. Она только запрещает отображение иерархической адресной книги в Outlook. Чтобы включить иерархическую адресную книгу с теми же параметрами конфигурации, следует просто включить корневую организацию.


Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-OrganizationConfig](https://technet.microsoft.com/ru-ru/library/aa997443\(v=exchg.150\)).

