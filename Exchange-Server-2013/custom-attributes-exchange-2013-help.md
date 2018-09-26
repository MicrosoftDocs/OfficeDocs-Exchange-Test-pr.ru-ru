---
title: 'Настраиваемые атрибуты: Exchange 2013 Help'
TOCTitle: Настраиваемые атрибуты
ms:assetid: 2b043878-0b34-4563-a9c2-28a9efa7447e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee423541(v=EXCHG.150)
ms:contentKeyID: 50487701
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настраиваемые атрибуты

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-17_

Microsoft Exchange Server 2013 предоставляет 15 атрибутов расширения. Эти атрибуты можно использовать для добавления сведений о получателе, например кода сотрудника, подразделения или другого пользовательского значения, для которого не существует атрибута. Эти настраиваемые атрибуты помечаются в Active Directory как атрибуты от **ms-Exch-Extension-Attribute1** до **ms-Exch-Extension-Attribute15**. В командной консоли Exchange соответствующими параметрами являются *CustomAttribute1*–*CustomAttribute15*. Эти атрибуты не используются компонентами Exchange. Они позволяют хранить данные Active Directory без необходимости расширения схемы Active Directory.

В Exchange Server 2003 и более ранних версиях, чтобы сохранить такие сведения в Active Directory, необходимо было создать атрибут и расширить схему Active Directory. Расширение схемы требовало планирования, получения идентификаторов объектов для новых атрибутов и проверки процесса расширения в тестовой среде перед его внедрением в производственной среде. В Exchange 2013 расширения схемы невозможно использовать в фильтрах получателей, используемых списками адресов, политиками адресов электронной почты и динамическими группами рассылки.

**Содержание**

Преимущества настраиваемых атрибутов

Примеры настраиваемых атрибутов

Пример настраиваемого атрибута с параметром ConditionalCustomAttributes

Пример настраиваемых атрибутов с использованием параметра ExtensionCustomAttributes

## Преимущества настраиваемых атрибутов

Ниже перечислены некоторые преимущества использования настраиваемых атрибутов.

  - Можно избежать расширения схемы Active Directory.

  - Атрибуты создаются с помощью программы установки Exchange.

  - Для управления атрибутами можно использовать центр администрирования Exchange (EAC) или командную консоль Exchange. Не требуется построение настраиваемых элементов управления и запись сценариев для заполнения и отображения этих атрибутов.

  - Эти атрибуты являются фильтруемыми свойствами, которые можно использовать в параметре *Filter* с командлетами получателей, например **Get-Mailbox**. Их также можно использовать в EAC и командной консоли Exchange для создания фильтров для политик адресов электронной почты, списков адресов и динамических групп рассылки.

## Многозначные настраиваемые атрибуты

В Exchange 2010 с пакетом обновлений 2 (SP2) добавлено пять многозначных настраиваемых атрибутов, которые позволяют вам хранить дополнительную информацию для получателей почты, если традиционные настраиваемые атрибуты не удовлетворяют ваши потребности. Параметрам *ExtensionCustomAttribute1*-*ExtensionCustomAttribute5* может быть присвоено до 1300 значений. Можно указать несколько значений в виде списка, разделенного запятыми. Следующие командлеты поддерживают эти новые параметры:

  - [Set-DistributionGroup](https://technet.microsoft.com/ru-ru/library/bb124955\(v=exchg.150\))

  - [Set-DynamicDistributionGroup](https://technet.microsoft.com/ru-ru/library/bb123796\(v=exchg.150\))

  - [Set-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123981\(v=exchg.150\))

  - [Set-MailContact](https://technet.microsoft.com/ru-ru/library/aa995950\(v=exchg.150\))

  - [Set-MailPublicFolder](https://technet.microsoft.com/ru-ru/library/bb123707\(v=exchg.150\))

  - [Set-RemoteMailbox](https://technet.microsoft.com/ru-ru/library/ff607302\(v=exchg.150\))

Дополнительные сведения о многозначных свойствах см. в разделе [Изменение многозначных свойств](modifying-multivalued-properties-exchange-2013-help.md).

## Примеры настраиваемых атрибутов

В различных развертываниях Exchange создание политики адресов электронной почты для всех получателей в подразделении является общим сценарием. Подразделение не является фильтруемым свойством, которое можно использовать в параметре *RecipientFilter* политики адресов электронной почты или списке адресов.

> [!NOTE]  
> Динамические группы рассылки имеют дополнительный параметр, который можно использовать для назначения их получателям определенного подразделения или контейнера.


Если получатели в этом подразделении не используют совместно какие-либо общие свойства, по которым можно выполнить фильтрацию, например отдел или местоположение, один из настраиваемых атрибутов можно заполнить общим значением, как показано в следующем примере.

```powershell
Get-Mailbox -OrganizationalUnit Sales | Set-Mailbox CustomAttribute1 "SalesOU"
```

Теперь можно создать политику адресов электронной почты для всех получателей, имеющих свойство *CustomAttribute1*, равное SalesOU, как показано в следующем примере.
```powershell
    New-EmailAddressPolicy -Name "Sales" -RecipientFilter { CustomAttribute1 -eq "SalesOU"} -EnabledEmailAddressTemplates "SMTP:%s%2g@sales.contoso.com"
```
## Пример настраиваемого атрибута с параметром ConditionalCustomAttributes

При создании динамических групп рассылки, политик адресов электронной почты или списков адресов не требуется использовать параметр *RecipeintFilter* для указания настраиваемых атрибутов. Для этого можно использовать параметры *ConditionalCustomAttribute1*–*ConditionalCustomAttribute15*.

Этот пример создает динамическую группу рассылки на основе получателей, значение *CustomAttribute1* которых равно SalesOU.
```powershell
    New-DynamicDistributionGroup -Name "Sales Users and Contacts" -IncludedRecipients "MailboxUsers,MailContacts" -ConditionalCustomAttribute1 "SalesOU"
```
> [!NOTE]  
> Параметр <em>IncludedRecipients</em> необходимо использовать при применении параметра <em>Conditional</em>. Кроме того, невозможно использовать параметры <em>Conditional</em>, если используется параметр <em>RecipientFilter</em>. Чтобы включить дополнительные фильтры для создания динамической группы рассылки, политик адресов электронной почты или списков адресов, необходимо использовать параметр <em>RecipientFilter</em>.


## Пример настраиваемых атрибутов с использованием параметра ExtensionCustomAttributes

В этом примере атрибут *ExtensionCustomAttribute1* почтового ящика для Kweku будет обновлен, чтобы указать, что пользователь зарегистрирован в следующих образовательных группах: MATH307, ECON202 и ENGL300.

```powershell
Set-Mailbox -Identity Kweku -ExtensionCustomAttribute1 MATH307,ECON202,ENGL300
```

Затем создается динамическая группа рассылки для всех студентов из группы MATH307 с помощью параметра *RecipientFilter*, где значение *ExtensionCustomAttribute1* равно MATH307. При использовании параметров *ExtentionCustomAttributes* можно использовать оператор `-eq` вместо оператора `-like`.
```powershell
    New-DynamicDistributionGroup -Name Students_MATH307 -RecipientFilter {ExtensionCustomAttribute1 -eq "MATH307"}
```
В этом примере значения *ExtensionCustomAttribute1* пользователя Kweku обновляются, чтобы указать, что он добавил группу ENGL210 и удалил ECON202.

```powershell
Set-Mailbox -Identity Kweku -ExtensionCustomAttribute1 @{Add="ENGL210"; Remove="ECON202"}
```

