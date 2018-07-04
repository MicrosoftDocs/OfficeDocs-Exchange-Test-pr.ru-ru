---
title: 'Справочник по разрешениям развертывания Exchange 2013: Exchange 2013 Help'
TOCTitle: Справочник по разрешениям развертывания Exchange 2013
ms:assetid: b13412d0-0cc4-4c1d-bf31-cae3d3e211a9
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee681663(v=EXCHG.150)
ms:contentKeyID: 59636085
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Справочник по разрешениям развертывания Exchange 2013

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

В этом разделе описываются разрешения, необходимые для настройки организации Microsoft Exchange Server 2013. Универсальные группы безопасности, связанные с группами ролей управления, а также другие группы и участники безопасности Windows добавляются в списки управления доступом (ACL) различных объектов Active Directory. С помощью списков управления доступом контролируются типы операций, которые можно выполнить над каждым объектом. Имея представление, какие разрешения предоставляются каждой группе ролей, группе или участнику безопасности, можно определить, какие минимальные разрешения необходимы для установки Exchange 2013.

В некоторых случаях список управления доступом применяется не к обычному свойству, **ntSecurityDescriptor**, а к другому свойству, например **msExchMailboxSecurityDescriptor**. Служба каталогов не может принудительно применить меры безопасности, не указанные в дескрипторе безопасности Windows. В большинстве случаев эти списки управления доступом реплицируются для сохранения списков управления доступом для соответствующих объектов с помощью службы хранилища. К сожалению, не существует средства просмотра этих списков управления доступом в виде, отличном от неформатированных двоичных данных.

Столбцы каждой таблицы разрешений включают указанные ниже данные.

  - **Учетная запись**   Участник безопасности, которому предоставлены или у которого отняты разрешения.

  - **Тип элемента управления доступом**   Тип элемента управления доступом (ACE)
    
      - **Разрешающий элемент управления доступом**   Разрешающий элемент управления доступом позволяет пользователю или группе, связанной с элементом управления доступом, обратиться к элементу.
    
      - **Запрещающий элемент управления доступом**   Запрещающий элемент управления доступом не позволяет пользователю или группе, связанной с элементом управления доступом, обратиться к элементу.

  - **Наследование**   Тип наследования, используемый для дочерних объектов.
    
      - **Все** показывает, что разрешения применяются к самому объекту и всем дочерним объектам.
    
      - **Убыв** показывает, что разрешения применяются к классу объектов, указанному в строке "К свойству".
    
      - **Нет** показывает, что разрешения применяются только к самому объекту.

  - **Разрешения**   Разрешения, предоставленные учетной записи.

  - **К свойству**   В некоторых случаях разрешения применяются только к заданному свойству, набору свойств или классу объектов. Эти ограниченные разрешения указываются здесь.

  - **Комментарии**   Если это возможно, в данном столбце объясняется необходимость применения разрешений или содержатся другие сведения о разрешениях.

Обычно разрешения перечислены в таблице по именам, используемым в редакторе ADSI (Active Directory Service Interfaces) (AdsiEdit.msc) на странице свойств **Безопасность** в режиме просмотра **Расширенный** на вкладке **Показать/Изменить**. На странице свойств **Безопасность** редактора ADSI разрешения приведены в более сжатом виде. Средство LDP (Ldp.exe) выводит маску доступа напрямую в виде численного значения. Код программы установки ссылается на разрешения по предопределенным константам.

В приведенной ниже таблице показаны соотношения между этими значениями.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Сводная страница редактора ADSI</th>
<th>Расширенный вид редактора ADSI, вкладка «Показать/Изменить»</th>
<th>Записи списка управления доступом, примененные к данному объекту</th>
<th>Двоичное значение (маска доступа в LDP)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Полный доступ</p></td>
<td><p>Полный доступ</p></td>
<td><p><code>WRITE_OWNER | WRITE_DAC | READ_CONTROL | DELETE | ACTRL_DS_CONTROL_ACCESS | ACTRL_DS_LIST_OBJECT | ACTRL_DS_DELETE_TREE | ACTRL_DS_WRITE_PROP | ACTRL_DS_READ_PROP | ACTRL_DS_SELF | ACTRL_DS_LIST | ACTRL_DS_DELETE_CHILD | ACTRL_DS_CREATE_CHILD</code></p></td>
<td><p><code>0x000F01FF</code></p></td>
</tr>
<tr class="even">
<td><p>Чтение</p></td>
<td><p>Вывод списка содержимого + Чтение всех свойств + Чтение разрешений</p></td>
<td><p><code>ACTRL_DS_LIST | ACTRL_DS_READ_PROP | READ_CONTROL</code></p></td>
<td><p><code>0x00020014</code></p></td>
</tr>
<tr class="odd">
<td><p>Запись</p></td>
<td><p>Запись всех свойств + Все проверенные операции записи</p></td>
<td><p><code>ACTRL_DS_WRITE_PROP | ACTRL_DS_SELF</code></p></td>
<td><p><code>0x00000028</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Вывод списка содержимого</p></td>
<td><p><code>ACTRL_DS_LIST</code></p></td>
<td><p><code>0x00000004</code></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Чтение всех свойств</p></td>
<td><p><code>ACTRL_DS_READ_PROP</code></p></td>
<td><p><code>0x00000010</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Запись всех свойств</p></td>
<td><p><code>ACTRL_DS_WRITE_PROP</code></p></td>
<td><p><code>0x00000020</code></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Удаление</p></td>
<td><p><code>DELETE</code></p></td>
<td><p><code>0x00010000</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Удаление поддерева</p></td>
<td><p><code>ACTRL_DS_DELETE_TREE</code></p></td>
<td><p><code>0x00000040</code></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Чтение разрешений</p></td>
<td><p><code>READ_CONTROL</code></p></td>
<td><p><code>0x00020000</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Изменение разрешений</p></td>
<td><p><code>WRITE_DAC</code></p></td>
<td><p><code>0x00040000</code></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Изменение владельца</p></td>
<td><p><code>WRITE_OWNER</code></p></td>
<td><p><code>0x00080000</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Все проверенные операции записи</p></td>
<td><p><code>ACTRL_DS_SELF</code></p></td>
<td><p><code>0x00000008</code></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Все расширенные права</p></td>
<td><p><code>ACTRL_DS_CONTROL_ACCESS</code></p></td>
<td><p><code>0x00000100</code></p></td>
</tr>
<tr class="even">
<td><p>Создание всех дочерних объектов</p></td>
<td><p>Создание всех дочерних объектов</p></td>
<td><p><code>ACTRL_DS_CREATE_CHILD</code></p></td>
<td><p><code>0x00000001</code></p></td>
</tr>
<tr class="odd">
<td><p>Удаление всех дочерних объектов</p></td>
<td><p>Удаление всех дочерних объектов</p></td>
<td><p><code>ACTRL_DS_DELETE_CHILD</code></p></td>
<td><p><code>0x00000002</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p></p></td>
<td><p><code>ACTRL_DS_LIST_OBJECT</code></p></td>
<td><p><code>0x00000080</code></p></td>
</tr>
</tbody>
</table>


Расширенные права — это настраиваемые права, заданные отдельными приложениями. Эти права указаны в списке управления доступом. Однако они не имеют смысла для Active Directory. Определенное приложение принудительно применяет все расширенные права. Примерами расширенных прав Exchange являются «Создание общей папки» и «Создание именованных свойств в банке данных».

Дополнительные сведения о разрешениях, устанавливаемых в процессе установки Exchange Server 2010, см. на веб-странице [Справка по разрешениям развертывания сервера Exchange 2010](https://go.microsoft.com/fwlink/p/?linkid=402924).

## Подготовка разрешений Active Directory

Таблицы разрешений, приведенные в данном разделе, показывают, какие разрешения устанавливаются при выполнении команды `Setup /PrepareAD`.

> [!NOTE]  
> В этом разделе описаны разрешения по умолчанию, используемые при развертывании Exchange 2013 с помощью общей модели разрешений. Если вы развернули Exchange 2013 с помощью модели разделенных разрешений Active Directory, разрешения по умолчанию будут другими. Дополнительные сведения об изменениях разрешений по умолчанию при использовании модели разделенных разрешений Active Directory, а также общую информацию о моделях общих и разделенных разрешений см. в разделе <a href="understanding-split-permissions-exchange-2013-help.md">Active Directory split permissions</a> статьи <a href="understanding-split-permissions-exchange-2013-help.md">Общие сведения о разделенных разрешениях</a>. Если при установке Exchange вы не выбрали разделенные разрешения Active Directory, Exchange будет использовать общие разрешения.


## Разрешения контейнера Microsoft Exchange

В приведенной ниже таблице показаны разрешения, установленные для контейнера Microsoft Exchange в разделе конфигурации.

### Различающееся имя объекта: CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\<домен\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Учетная запись установки</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p></p></td>
<td><p>Это учетная запись, используемая для выполнения команды <code>/PrepareAD</code>.</p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Нет</p></td>
<td><p>Чтение свойства</p>
<p>Список содержимого</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение разрешений</p></td>
<td><p>msExchSmtpRceiveConnector</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Делегированная установка</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Разрешения контейнера автообнаружения Microsoft Exchange

В следующей таблице показаны разрешения, установленные для контейнера автообнаружения Microsoft Exchange в разделе конфигурации.

### Различающееся имя объекта: CN=Microsoft Exchange Autodiscover,CN=Services,CN=Configuration,DC=\<домен\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Разрешения контейнера организации Microsoft Exchange

В таблицах разрешений, приведенных в этом разделе, показаны разрешения, установленные для организации Майкрософт Exchange и вложенных контейнеров в разделе конфигурации.

### Различающееся имя объекта: CN=\<организация\>,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\<домен\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетные записи</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Администраторы предприятия</p>
<p>Администраторы корневого домена</p>
<p>Учетная запись установки</p>
<p>Управление организацией</p></td>
<td><p>Запрещающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить как</p>
<p>Получить как</p></td>
<td><p></p></td>
<td><p>Администраторам Windows не разрешается открывать почтовые ящики.</p></td>
</tr>
<tr class="even">
<td><p>Администраторы предприятия</p>
<p>Администраторы схемы</p>
<p>Администраторы корневого домена</p>
<p>Учетная запись установки</p>
<p>Управление организацией</p></td>
<td><p>Запрещающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Олицетворение веб-служб Exchange</p>
<p>Сериализация маркера веб-служб Exchange</p></td>
<td><p></p></td>
<td><p>Расширенное право</p></td>
</tr>
<tr class="odd">
<td><p>Администраторы предприятия</p>
<p>Администраторы схемы</p>
<p>Администраторы корневого домена</p>
<p>Учетная запись установки</p></td>
<td><p>Запрещающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Доступ к транспорту хранилища</p>
<p>Ограниченное делегирование хранилища</p>
<p>Доступ к хранилищу на чтение</p>
<p>Доступ к хранилищу на чтение и запись</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Локальная система</p></td>
<td><p>Разрешить</p></td>
<td><p>Все</p></td>
<td><p>Все расширенные права</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Запрещающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>msExchAvailabilityUserPassword / msExchAvailabilityAddressSpace</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешить</p></td>
<td><p>Нет</p></td>
<td><p>Чтение</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>NT Authority\Сетевая служба</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управляемые серверы доступности</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Все расширенные права</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>groupType</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchOwningServer</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchMailboxSecurityDescriptor</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMServerWritableFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchDatabaseCreated</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUserCulture</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchMobileMailboxFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>siteFolderGUID</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>siteFolderServer</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchEDBOffline</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>userCertificate</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMDtmfMap</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchBlockedSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Public Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchPatchMDB</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>publicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMSpokenName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMPinChecksum</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>legacyExchangeDN</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchSafeSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>thumbnailPhoto</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание общей папки верхнего уровня</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание общей папки верхнего уровня</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Просмотр состояния банка данных</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Просмотр состояния банка данных</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Администрирование банка данных</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Администрирование банка данных</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание именованных свойств в банке данных</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание именованных свойств в банке данных</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение списка управления доступом к общим папкам</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение списка управления доступом к общим папкам</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение квот общих папок</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение квот общих папок</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение административного списка управления доступом к общим папкам</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение административного списка управления доступом к общим папкам</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение срока действия общих папок</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение срока действия общих папок</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение списка реплик общих папок</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение списка реплик общих папок</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение срока хранения удаленного элемента общей папки</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение срока хранения удаленного элемента общей папки</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание общей папки</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание общей папки</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Общая папка с доступом к почте</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Все</p>
<p>NT Authority\Анонимный вход</p>
<p></p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание именованных свойств в банке данных</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Все</p>
<p>NT Authority\Анонимный вход</p>
<p></p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание общей папки</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Все</p>
<p>NT Authority\Анонимный вход</p>
<p></p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p><code>/ msExchPrivateMDB</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Все</p>
<p>NT Authority\Анонимный вход</p>
<p></p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p><code>/ msExchPublicMDB</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p><code>/ siteAddressing</code></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=All Address Lists,CN=Address Lists Container,CN=\<организация\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Список содержимого</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchLastAppliedRecipientFilter</code></p>
<p><code>msExchRecipientFilterFlags</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchLastAppliedRecipientFilter</code></p>
<p><code>msExchRecipientFilterFlags</code></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Offline Address Lists,CN=Address Lists Container, CN=\<организация\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Загрузка автономной адресной книги</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Addressing,CN=\<организация\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Recipient Policies,CN=\<организация\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchLastAppliedRecipientFilter</code></p>
<p><code>msExchRecipientFilterFlags</code></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchLastAppliedRecipientFilter</code></p>
<p><code>msExchRecipientFilterFlags</code></p></td>
</tr>
</tbody>
</table>


## Разрешения контейнера раздела конфигурации

В таблицах разрешений, приведенных в этом разделе, показаны разрешения, установленные с помощью команды `Setup /PrepareAD` на различных контейнерах в разделе конфигурации.

### Различающееся имя объекта: CN=Sites,CN=Configuration,DC=\<домен\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchVersion / site</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchVersion / site-link</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchPartnerId / site</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchMinorPartnerId / site</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchResponsibleforSites / site</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p></p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchTransportSiteFlags / site</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchCost / site-link</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p>
<p>Локальная система</p>
<p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p><code>/ msExchEdgeSyncEHFConnector</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p>
<p>Локальная система</p>
<p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p><code>/ msExchEdgeSyncMservConnector</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Дочерние объекты</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p>
<p>Удаление дерева</p></td>
<td><p><code>msExchEdgeSyncServiceConfig / site</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p>
<p>Локальная система</p>
<p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p><code>/ msExchEdgeSyncServiceConfig</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Дочерние объекты</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p>
<p>Удаление дерева</p></td>
<td><p><code>msExchEdgeSyncMservConnector / msExchEdgeSyncServiceConfig</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p>
<p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Дочерние объекты</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p>
<p>Удаление дерева</p></td>
<td><p><code>msExchEdgeSyncEHFConnector / msExchEdgeSyncServiceConfig</code></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Deleted Objects,CN=Configuration,DC=\<домен\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Список содержимого</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Администрирование организации</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Учетная запись установки</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешения</p>
<p>Запись разрешения</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p>Это учетная запись, используемая для выполнения команды <code>/PrepareAD</code>.</p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Сетевая служба</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Список содержимого</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Разрешения административной группы Exchange

Команда `Setup /PrepareAD` также настраивает для административных групп в организации указанные ниже разрешения.

### Различающееся имя объекта: CN=\<административная группа\>,CN=Administrative Groups,CN=\<организация\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Доступ к службе обновления получателей</p></td>
<td><p><code>msExchExchangeServer</code></p></td>
<td><p>Разрешает администраторам получателей Exchange отмечать получателей, указывая сведения об адресе прокси-сервера.</p></td>
</tr>
<tr class="even">
<td><p>Локальная система</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Доступ к службе обновления получателей</p></td>
<td><p><code>msExchExchangeServer</code></p></td>
<td><p>Разрешает серверам отмечать получателей, указывая сведения об адресе прокси-сервера.</p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Доступ к службе обновления получателей</p></td>
<td><p><code>msExchExchangeServer</code></p></td>
<td><p>Разрешает администраторам общих папок Exchange указывать для получателей сведения об адресе прокси-сервера.</p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Advanced Security Settings,CN=\<административная группа\>,CN=Administrative Groups,CN=\<организация\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Нет</p></td>
<td><p>Список содержимого</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Encryption,CN=Advanced Security Settings,CN=\<административная группа\>,CN=Administrative Groups,CN=\<организация\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Нет</p></td>
<td><p>Чтение свойства</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Arrays,CN=\<административная группа\>,CN=Administrative Groups,CN=\<организация\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Нет</p></td>
<td><p>Список содержимого</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Database Availability Groups,CN=\<административная группа\>,CN=Administrative Groups,CN=\<организация\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Нет</p></td>
<td><p>Список содержимого</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Databases,CN=\<административная группа\>,CN=Administrative Groups,CN=\<организация\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Нет</p></td>
<td><p>Список содержимого</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Servers,CN=\<административная группа\>,CN=Administrative Groups,CN=\<организация\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Запрещающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Получить как</p></td>
<td><p></p></td>
<td><p>Серверам Exchange не разрешается открывать почтовые ящики.</p></td>
</tr>
<tr class="even">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Нет</p></td>
<td><p>Список содержимого</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Разрешения контейнера групп безопасности Microsoft Exchange

В таблицах разрешений, приведенных в этом разделе, показаны разрешения, установленные для контейнера групп безопасности Майкрософт Exchange в разделе корневого домена.

### Различающееся имя объекта: OU=Microsoft Exchange Security Groups,DC=\<корневой домен\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p></td>
<td><p><code>/ Group</code></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Удаление</p></td>
<td><p><code>/ group</code></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Member / group</code></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Organization Management,OU=Microsoft Exchange Security Groups,DC=\<корневой домен\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Public Folder Management,OU=Microsoft Exchange Security Groups,DC=\<корневой домен\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=ExchangeLegacyInterop,OU=Microsoft Exchange Security Groups,DC=\<корневой домен\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Exchange Servers,OU=Microsoft Exchange Security Groups,DC=\<корневой домен\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Администраторы корневого домена</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Члены с правами на чтение</p>
<p>Члены с правами на запись</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Администраторы дочернего домена</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Члены с правами на чтение</p>
<p>Члены с правами на запись</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Подготовка домена

В следующих таблицах показаны разрешения, установленные при выполнении команды `Setup /PrepareDomain`.

> [!NOTE]  
> В этом разделе описаны разрешения по умолчанию, используемые при развертывании Exchange 2013 с помощью общей модели разрешений. Если вы развернули Exchange 2013 с помощью модели разделенных разрешений Active Directory, разрешения по умолчанию будут другими. Дополнительные сведения об изменениях разрешений по умолчанию при использовании модели разделенных разрешений Active Directory, а также общую информацию о моделях общих и разделенных разрешений см. в разделе <a href="understanding-split-permissions-exchange-2013-help.md">Active Directory split permissions</a> статьи <a href="understanding-split-permissions-exchange-2013-help.md">Общие сведения о разделенных разрешениях</a>. Если при установке Exchange вы не выбрали разделенные разрешения Active Directory, Exchange будет использовать общие разрешения.


### Различающееся имя объекта: DC=\<домен\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>NT AUTHORITY\СЕТЬ</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p>Предоставляет транспортной службе разрешения на чтение.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>groupType</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchMailboxSecurityDescriptor</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMServerWritableFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUserCultulre</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>memberOf</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>userAccountControl</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>canonicalName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Синхронизация репликации</p></td>
<td><p></p></td>
<td><p>Расширенное право</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p>
<p>Вывод списка дочерних объектов</p></td>
<td><p><code>msExchActiveSyncDevices / User</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p>
<p>Вывод списка дочерних объектов</p></td>
<td><p><code>msExchActiveSyncDevices / inetOrgPerson</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchSafeSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchMobileMailboxFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchSafeRecipientsHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>userCertificate</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMDtmfMap</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchBlockedSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMSpokenName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMPinChecksum</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>thumbnailPhoto</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>legacyExchangeDN</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>textEncodedORAddress</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>proxyAddresses</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>mail</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>displayNamePrintable</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>showInAddressBook</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p><code>/ msExchDynamicDistributionList</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>adminDisplayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>displayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>displayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Public Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>adminDisplayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p><code>/ msExchDynamicDistributionList</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>textEncodedORAddress</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>showInAddressBook</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>legacyExchangeDN</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>proxyAddresses</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>displayNamePrintable</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>mail</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>pwdLastSet</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>WriteDACL</p></td>
<td><p><code>/ user</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>WriteDACL</p>
<p></p></td>
<td><p><code>/ inetOrgPerson</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Удаление дерева</p></td>
<td><p><code>/ user</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Удаление дерева</p>
<p></p></td>
<td><p><code>/ inetOrgPerson</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>sAMAccountName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление</p></td>
<td><p><code>/ contact</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление</p></td>
<td><p><code>/ inetOrgPerson</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление</p></td>
<td><p><code>/ user</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление</p></td>
<td><p><code>/ organizationUnit</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление</p></td>
<td><p><code>/ group</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p></td>
<td><p><code>/ computer</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Member</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>wwwHomePage</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>countryCode</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>userAccountControl</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>managedBy</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Сброс пароля при следующем входе в систему</p></td>
<td><p></p></td>
<td><p>Расширенное право</p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Изменение пароля</p></td>
<td><p><code> / user</code></p></td>
<td><p>Расширенное право</p></td>
</tr>
<tr class="odd">
<td><p>Делегированная установка</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>User Account Restrictions</code></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=AdminSDHolder,CN=System,DC=\<домен\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>NT AUTHORITY\СЕТЬ</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p>Предоставляет транспортной службе разрешения на чтение.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>groupType</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchMailboxSecurityDescriptor</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMServerWritableFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUserCultulre</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>memberOf</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>userAccountControl</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>canonicalName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Синхронизация репликации</p></td>
<td><p></p></td>
<td><p>Расширенное право</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p>
<p>Вывод списка дочерних объектов</p></td>
<td><p><code>msExchActiveSyncDevices / User</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p>
<p>Вывод списка дочерних объектов</p></td>
<td><p><code>msExchActiveSyncDevices / inetOrgPerson</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchSafeSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchMobileMailboxFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchSafeRecipientsHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>userCertificate</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMDtmfMap</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchBlockedSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMSpokenName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchUMPinChecksum</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>thumbnailPhoto</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>legacyExchangeDN</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>textEncodedORAddress</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>proxyAddresses</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>mail</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>displayNamePrintable</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>showInAddressBook</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p><code>/ msExchDynamicDistributionList</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>adminDisplayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>displayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>displayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Public Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>adminDisplayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p><code>/ msExchDynamicDistributionList</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>textEncodedORAddress</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>showInAddressBook</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>legacyExchangeDN</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>proxyAddresses</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>displayNamePrintable</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>mail</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>pwdLastSet</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>sAMAccountName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>Member</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>wwwHomePage</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>countryCode</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>userAccountControl</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Разрешения Windows для Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>managedBy</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Делегированная установка</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>User Account Restrictions</code></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Deleted Objects,DC=\<домен\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Список содержимого</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Microsoft Exchange System Objects,DC=\<домен\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NT AUTHORITY\СЕТЬ</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p>
<p>Список содержимого</p>
<p>Чтение разрешений</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
</tr>
<tr class="even">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>adminDisplayName</code></p></td>
</tr>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>modifyTimeStamp</code></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Запрещающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Удаление дерева</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства Удаление дерева</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p></p></td>
<td><p><code>/ msExchSystemMailbox</code></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p></td>
<td><p><code>/ publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p></p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Удаление дочернего объекта</p>
<p></p></td>
<td><p><code>/ msExchSystemMailbox</code></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Удаление дочернего объекта</p>
<p></p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>/ publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>/ msExchSystemMailbox</code></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Смена пароля</p>
<p>Сброс пароля при следующем входе в систему</p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>/ msExchSystemMailbox</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p></td>
<td><p><code>/ msExchSystemMailbox</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>mail / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>displayNamePrintable / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>displayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>textEncodedORAddress / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>proxyAddresses / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>cn / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>showInAddressBook / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>Exchange Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p>legacyExchangeDN / publicFolder</p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>Exchange Personal Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>msDSPhoneticDisplayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>msExchPFContacts / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>garbageCollPeriod / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>name / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>msExchPublicDelegates / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>mail / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>displayNamePrintable / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>displayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>textEncodedORAddress / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>proxyAddresses / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>cn / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>showInAddressBook / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>Exchange Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>legacyExchangeDN / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>Exchange Personal Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>msDSPhoneticDisplayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>msExchPFContacts / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>garbageCollPeriod / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>name / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Управление общими папками</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>msExchPublicDelegates / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>mail / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>displayNamePrintable / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>displayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>textEncodedORAddress / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>proxyAddresses / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>cn / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>showInAddressBook / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>Exchange Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>legacyExchangeDN / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>Exchange Personal Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>msDSPhoneticDisplayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>msExchPFContacts / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>garbageCollPeriod / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>name / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Группа безопасности Exchange Trusted Subsystem</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p>
<p>Запись свойства</p></td>
<td><p><code>msExchPublicDelegates / publicFolder</code></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Exchange Install Domain Servers,CN=Microsoft Exchange System Objects,DC=\<домен\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Управление организацией</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Установка роли сервера

При установке ролей сервера клиентского доступа и сервера почтовых ящиков программа установки добавляет универсальную группу безопасности "Управление организацией" в административную группу безопасности на локальном компьютере. Это позволяет участникам группы ролей управления с именем "Управление организацией" управлять сервером.

В следующей таблице показаны разрешения, устанавливаемые при установке ролей сервера клиентского доступа или сервера почтовых ящиков.

### Различающееся имя объекта: CN=\<сервер\>,CN=Servers,CN=\<административная группа\>,CN=Administrative Groups,CN=\<организация\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MACHINE$</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>MACHINE$</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Нет</p></td>
<td><p>Запись свойства</p></td>
<td><p><code>msExchServerSite</code></p>
<p><code>msExchEdgeSyncCredential</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Доступ к транспорту хранилища</p>
<p>Ограниченное делегирование хранилища</p>
<p>Доступ к хранилищу только для чтения</p>
<p>Доступ к хранилищу на чтение и запись</p></td>
<td><p></p></td>
<td><p>Расширенные права</p></td>
</tr>
<tr class="even">
<td><p>NT AUTHORITY\СЕТЬ</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Сериализация маркера веб-служб Exchange</p></td>
<td><p></p></td>
<td><p>Расширенное право</p>
<p>Объекты роли, предоставляемые только на сервере почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>NT AUTHORITY\СЕТЬ</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Локальная система</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение разрешений</p>
<p>Список содержимого</p>
<p>Чтение свойства</p>
<p>Список объектов</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Делегированная установка</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Полный доступ</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Делегированная установка</p></td>
<td><p>Запрещающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Создание дочернего объекта</p>
<p>Удаление дочернего объекта</p></td>
<td><p><code>/ msExchPublicMDB</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Чтение свойства</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Делегированная установка</p></td>
<td><p>Запрещающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Получить как</p>
<p>Отправить как</p></td>
<td><p></p></td>
<td><p>Расширенное право</p></td>
</tr>
</tbody>
</table>


## Группы доступности базы данных

В таблицах разрешений, приведенных в этом разделе, показаны разрешения, установленные для групп доступности базы данных и их участников.

### Различающееся имя объекта: CN=\<DAGName\>,CN=Database Availability Groups,CN=\<административная группа\>,CN=Administrative Groups,CN=\<организация\>

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Нет</p></td>
<td><p>Чтение свойства</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Пограничный транспортный сервер

При установке пограничного транспортного сервера и установлении пограничной подписки с организацией Exchange устанавливаются разрешения из приведенной ниже таблицы разрешений.

### Различающееся имя объекта: CN=\<сервер\>,CN=Servers,CN=\<административная группа\>,CN=Administrative Groups,CN=\<организация\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Запись свойства</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Нет</p></td>
<td><p>Чтение свойств</p></td>
<td><p></p></td>
<td><p>Элемент управления доступом определен в схеме для класса <code>msExchExchangeServer</code> объектов <code>defaultSecurityDescriptor</code>.</p></td>
</tr>
</tbody>
</table>


## Установка сервера почтовых ящиков

Во время установки первого сервера почтовых ящиков создаются следующие контейнеры, если они не существуют. В приведенной ниже таблице разрешений показаны применяемые разрешения.

### Различающееся имя объекта: CN=Availability Configuration,CN=\<организация\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Убыв</p></td>
<td><p>Чтение свойства</p></td>
<td><p><code>msExchAvailabilityUserPassword / msExchAvailabilityAddressSpaceObjects</code></p></td>
<td><p>Расширенное право</p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Default \<сервер\>,CN=SMTP Receive Connectors,CN=Protocols,CN=\<сервер\>,CN=Servers,CN=\<административная группа\>,CN=\<организация\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Запрещающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки леса</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Запрещающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки организации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать любого отправителя</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать любого отправителя</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать любого отправителя</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности (SID) для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать любого отправителя</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать любого отправителя</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать EXCH50</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать EXCH50</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать EXCH50</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать EXCH50</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать EXCH50</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Прием XShadow</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Прием XShadow</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSessionParams</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSessionParams</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSessionParams</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки леса</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять xAttr</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять xAttr</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять xAttr</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Accept XProxyFrom</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XProxyFrom леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XProxyFrom леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSysProbe</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSysProbe леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSysProbe леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить расширенные свойства XMessageContext</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить расширенные свойства XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить расширенные свойства XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить индекс Fast XMessageContext</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить индекс Fast XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить индекс Fast XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить кэш получателя AD XMessageContext</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить кэш получателя AD XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить кэш получателя AD XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать флаг проверки подлинности</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать флаг проверки подлинности</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать флаг проверки подлинности</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать флаг проверки подлинности</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать флаг проверки подлинности</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить предел размера сообщения</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить предел размера сообщения</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить предел размера сообщения</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить предел размера сообщения</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить предел размера сообщения</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки организации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки организации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки организации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать отправителей доверенного домена</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать отправителей доверенного домена</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать отправителей доверенного домена</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать отправителей доверенного домена</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать отправителей доверенного домена</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### Различающееся имя объекта: CN=Client \<сервер\>,CN=SMTP Receive Connectors,CN=Protocols,CN=\<сервер\>,CN=Servers,CN=\<административная группа\>,CN=\<организация\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Пользователи, прошедшие проверку</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSessionParams</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSessionParams</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSessionParams</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать любого отправителя</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать любого отправителя</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности (SID) для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать любого отправителя</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать любого отправителя</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать Exch50</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать Exch50</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать Exch50</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать Exch50</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения любому получателю</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Прием XShadow</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Прием XShadow</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки леса</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять xAttr</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять xAttr</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять xAttr</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Accept XProxyFrom</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XProxyFrom леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XProxyFrom леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать флаг проверки подлинности</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать флаг проверки подлинности</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать флаг проверки подлинности</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать флаг проверки подлинности</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSysProbe</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSysProbe леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принять XSysProbe леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать флаг проверки подлинности</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить защиту от нежелательной почты</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить расширенные свойства XMessageContext</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить расширенные свойства XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить расширенные свойства XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить индекс Fast XMessageContext</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить индекс Fast XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить индекс Fast XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить предел размера сообщения</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить предел размера сообщения</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить предел размера сообщения</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Обходить предел размера сообщения</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки организации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки организации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать заголовки организации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить кэш получателя AD XMessageContext</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить кэш получателя AD XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправить кэш получателя AD XMessageContext</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять сообщения серверу</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать отправителей доверенного домена</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать отправителей доверенного домена</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать отправителей доверенного домена</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Принимать отправителей доверенного домена</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Создание соединителя отправки SMTP

В следующей таблице показаны разрешения, устанавливаемые при создании соединителей отправки.

### Различающееся имя объекта: CN=\<имя соединителя\>,CN=Connections,CN=\<группа маршрутизации\>,CN=Routing Groups, CN=\<административная группа\>,CN=\<организация\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Учетная запись</th>
<th>Тип элемента управления доступом</th>
<th>Наследование</th>
<th>Разрешения</th>
<th>К свойству</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NT AUTHORITY\АНОНИМНЫЙ ВХОД</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки организации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки организации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки организации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки леса</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправка XShadow</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправка XShadow</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправка XShadow</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-10</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов-партнеров.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-24</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправлять заголовки маршрутизации</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для устаревших серверов Exchange.</p></td>
</tr>
<tr class="odd">
<td><p>Серверы Exchange</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправка Exch50</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправка Exch50</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для серверов почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправка Exch50</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для пограничных транспортных серверов.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправка Exch50</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности серверов с внешней защитой.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-24</p></td>
<td><p>Разрешающий элемент управления доступом</p></td>
<td><p>Все</p></td>
<td><p>Отправка Exch50</p></td>
<td><p></p></td>
<td><p>Это известный идентификатор безопасности для устаревших серверов Exchange.</p></td>
</tr>
</tbody>
</table>

