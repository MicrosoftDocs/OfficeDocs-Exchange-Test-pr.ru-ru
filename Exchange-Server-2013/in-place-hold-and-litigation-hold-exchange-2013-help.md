﻿---
title: 'Хранение на месте и хранение для судебного разбирательства: Exchange 2013 Help'
TOCTitle: Хранение на месте и хранение для судебного разбирательства
ms:assetid: 71031c06-852d-44d8-b558-dff444eaef8c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff637980(v=EXCHG.150)
ms:contentKeyID: 50488212
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Хранение на месте и хранение для судебного разбирательства

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2017-11-15_

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Мы перенесли дату, до которой можно создавать удержания на месте в Exchange Online (в Office 365 и автономных планах Exchange Online), с 1 июля 2017 г. на более поздний срок. Но до конца года или в начале следующего этой возможности в Exchange Online не станет. В качестве альтернативы можно использовать <a href="https://go.microsoft.com/fwlink/?linkid=780738">дела обнаружения электронных данных</a> или <a href="https://go.microsoft.com/fwlink/?linkid=827811">политики хранения</a> в Центре безопасности и соответствия требованиям Office 365. После этого вы по-прежнему сможете изменять существующие удержания на месте и создавать новые в гибридных развертываниях Exchange Server 2013 и Exchange. И вы по-прежнему сможете помещать почтовые ящики на хранение для судебного разбирательства.</td>
</tr>
</tbody>
</table>


При наличии обоснованных предпосылок для судебных исков организациям требуется сохранять электронные данные (включая почту), связанные с делом. Такие предпосылки нередко возникают до уточнения подробностей дела, и сохранение часто имеет широкие масштабы. Организациям может понадобиться сохранять всю почту, относящуюся к конкретному вопросу, или всю электронную почту отдельных лиц. В зависимости от политики организации в отношении обнаружения электронных данных, можно принять следующие меры по сохранению электронной почты.

  - Пользователям можно порекомендовать хранить почту, не удаляя сообщения. Однако пользователи все же могут удалять электронную почту намеренно или случайно.

  - Могут быть приостановлены механизмы автоматического удаления, например управление записями обмена сообщениями. Это может привести к тому, что в почтовых ящиках пользователей будет скапливаться большой объем электронной почты, из-за чего производительность их работы может снижаться. Приостановка автоматического удаления также не мешает пользователям вручную удалять электронную почту.

  - В некоторых организациях электронная почта копируется или перемещается в архив, что позволяет предотвратить ее удаление, изменение или подмену. Это ведет к повышению расходов, обусловленных необходимостью ручного копирования или перемещения сообщений в архив или внедрения сторонних продуктов для сбора и хранения электронной почты вне Exchange.

Отсутствие возможности хранения электронной переписки может подвергнуть организацию юридическим и финансовым рискам, например к критическому анализу процессов обнаружения и хранения записей в организации, неблагоприятным судебным решениям, санкциям или штрафам.

С помощью хранения на месте и хранения для судебного разбирательства можно решать следующие задачи:

  - Помещать почтовые ящики пользователей на хранение и хранить их элементы без изменений.

  - Хранить элементы почтовых ящиков, удаленные вручную или автоматически, например службой управления записями сообщений.

  - Использовать хранение на месте на основе запросов для поиска и хранения элементов, соответствующих определенным условиям.

  - Хранить элементы бесконечно или в течение заданного периода времени.

  - Устанавливать несколько запретов на удаление для разных дел или расследований.

  - Скрывать запреты на удаление от пользователя, так как работа службы управления записями сообщений не прерывается.

  - Включать поиск с обнаружением электронных данных на месте для элементов, помещенных на хранение.

**Содержание**

Сценарии хранения на месте

Хранение на месте и хранение для судебного разбирательства

Включение для почтового ящика удержания на месте

Помещение общедоступных папок на удержание

Запреты на удаление и папка корзины

Запреты на удаление и квоты почтового ящика

Запреты на удаление и пересылка электронной почты

Хранение архивированного содержимого Lync

Удаление почтового ящика на хранении

Перенос почтовых ящиков на хранении из Exchange 2013 в Office 365

## Сценарии хранения на месте

В Exchange Server 2010 понятие удержания по юридическим причинам обозначает ситуации, когда все данные почтовых ящиков для пользователя удерживаются в течение неопределенного периода времени или до снятия с удержания. В Exchange 2013 представлена новая модель удержания на месте, которая позволяет задать следующие параметры.

  - **Элементы для хранения**.   Вы можете указать, какие элементы необходимо поместить на хранение, используя такие параметры запроса, как ключевые слова, отправители и получатели, даты начала и окончания, а также указать типы сообщений, например сообщения электронной почты или элементы календаря.

  - **Продолжительность хранения**.   Вы можете указать продолжительность хранения для элементов.

С помощью этой новой модели удержание на месте позволяет создавать структурированные политики удержания, чтобы сохранять элементы почтовых ящиков в следующих случаях:

  - **Бесконечное хранение**.   Сценарий неограниченного хранения похож на сценарий хранения для судебного разбирательства. Этот сценарий предназначен для хранения элементов почтового ящика в соответствии с требованиями к обнаружению электронных данных. В период судебного разбирательства или расследования элементы не удаляются. Длительность неизвестна заранее, поэтому дата окончания не настроена. Чтобы хранить все элементы почты в течение неопределенного периода времени, не указывайте параметры запроса или длительность при создании хранения на месте.

  - **Хранение на основе запроса**. Если в организации элементы хранятся на основе указанных параметров запроса, можно использовать хранение на месте на основе запроса. Вы можете указать такие параметры запроса, как ключевые слова, даты начала и окончания, адреса отправителей и получателей, а также типы сообщений. После создания удержания на месте на основе запроса сохраняются все соответствующие параметрам запроса элементы почтового ящика (как существующие, так и создаваемые в будущем, включая сообщения, которые будут получены позже).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Сохраняются и элементы, которые помечены как не включаемые в поиск (обычно из-за ошибки при индексировании вложения). Это происходит потому, что невозможно определить, соответствуют ли они параметрам запроса. Дополнительные сведения об элементе, не включаемом в поиск, см. в разделе <a href="unsearchable-items-in-exchange-ediscovery-exchange-2013-help.md">Элементы, которые не включены в поиск при обнаружении электронных данных Exchange</a>.</td>
    </tr>
    </tbody>
    </table>


  - **Хранение с учетом времени**.   При хранении на месте и хранении для судебного разбирательства можно указывать период времени, в течение которого нужно хранить элементы. Этот срок рассчитывается с даты получения или создания элемента почтового ящика.
    
    Если в организации требуется, чтобы все элементы хранились на протяжении определенного периода, например 7 лет, можно создать удержание на основе времени. В Exchange 2013 можно задать срок хранения элементов на удержании. Возраст элементов на удержании вычисляется с даты их получения. Например, рассмотрим почтовый ящик в режиме удержания на месте на основе времени со сроком хранения 365 дней. Если элемент в этом почтовом ящике удаляется через 300 дней после даты получения, он удерживается еще 65 дней, прежде чем будет окончательно удален. Хранение на месте с учетом времени можно использовать в сочетании с политикой хранения, чтобы элементы гарантированно сохранялись в течение указанного периода и окончательно удалялись после его завершения.

При удержании на месте можно указать для пользователя несколько сценариев удержания. В этом случае поисковые запросы от сценариев удержания по запросу объединяются (с помощью операторов **OR**). При этом максимальное количество ключевых слов во всех сценариях удержания по запросу, назначенных для почтового ящика, не должно превышать 500. Если ключевых слов больше, на удержание помещается все содержимое почтового ящика, а не только то, которое соответствует критериям поиска. Все содержимое удерживается, пока количество ключевых слов не станет равно или меньше 500.

К началу

## Хранение на месте и хранение для судебного разбирательства

Хранение для судебного разбирательства, функция удержания, представленная в Exchange 2010 для сохранения и обнаружения электронных данных, доступна и в Exchange 2013. При хранении для судебного разбирательства используется свойство **LitigationHoldEnabled** почтового ящика. При хранении на месте можно задать различные условия удержания, применяя параметры запросов и используя одновременно несколько сценариев хранения. А хранение для судебного разбирательства позволяет только поставить все элементы на удержание. Когда к почтовому ящику применяется хранение для судебного разбирательства, вы также можете указать период удержания. Этот срок рассчитывается с даты получения или создания элемента почтового ящика. Если вы не укажете этот период, элементы будут удерживаться бесконечно или до тех пор, пока сценарий хранения не будет удален.

Когда для почтового ящика одновременно заданы один или несколько сценариев хранения на месте и сценарий хранения для судебного разбирательства (без указания периода), все элементы удерживаются бесконечно или до тех пор, пока сценарии хранения не будут удалены. Если вы удалите сценарий хранения для судебного разбирательства, а для пользователя останутся заданными один или несколько сценариев хранения на месте, элементы, соответствующие условиям таких сценариев, будут удерживаться в течение периода, указанного в параметрах хранения. Если после применения к почтовому ящику хранения для судебного разбирательства в Exchange 2010 вы переместите этот почтовый ящик на сервер почтовых ящиков Exchange 2013, параметры хранения для судебного разбирательства будут продолжать действовать. Это обеспечит соответствие требованиям во время и после перемещения.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если вы задаете для почтового ящика хранение на месте или хранение для судебного разбирательства, удержание распространяется как на основной, так и на архивный почтовые ящики. Если вы задаете для основного почтового ящика, размещенного на локальном сервере, хранение в гибридной среде Exchange, архивный почтовый ящик в облаке (если он включен) также помещается на хранение.</td>
</tr>
</tbody>
</table>


Дополнительные сведения см. в следующих разделах:

  - [Перевод почтового ящика в режим хранения для судебного разбирательства](place-a-mailbox-on-litigation-hold-exchange-2013-help.md)

  - [Применение функции хранения ко всем почтовым ящикам](place-all-mailboxes-on-hold-exchange-2013-help.md)

## Включение для почтового ящика удержания на месте

Полномочные пользователи, добавленные в группу ролей управления доступом на основе ролей [Управление обнаружением](discovery-management-exchange-2013-help.md) или которым назначены роли управления удержанием по юридическим причинам или поиском в почтовых ящиках, могут перевести пользователей почтовых ящиков в режим на удержания на месте. Эту задачу можно делегировать диспетчерам записей, ответственным за обеспечение соответствия требованиям, или юристам организации, предоставляя при этом минимально необходимый уровень привилегий. Дополнительные сведения о назначении группы ролей Управление обнаружением см. в разделе [Назначение разрешений обнаружения электронных данных в Exchange](assign-ediscovery-permissions-in-exchange-exchange-2013-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В Exchange 2010 роль удержания по юридическим причинам предоставила пользователям достаточно разрешений на применение к почтовым ящикам хранения для судебного разбирательства. В Exchange 2013 то же разрешение можно использовать для размещения почтовых ящиков в режим удержания на месте в течение неопределенного периода времени или на основе времени. Однако, чтобы создать на основе запроса на месте удержание, пользователю должна быть назначена роль поиска в почтовых ящиках. То есть обе эти группы ролей Управление обнаружением ролей.</td>
</tr>
</tbody>
</table>


В Exchange 2013, на месте функциональность интегрируется с удержания на месте операции поиска eDiscovery. Можно использовать **на месте eDiscovery & держаться** мастера в Exchange центр администрирования (EAC) или **New-MailboxSearch** и связанных с ней командлетов в Exchange командной консоли для помещения почтового ящика на удержание на месте. Дополнительные сведения см. в разделе [Создание или удаление инцидента хранения на месте](create-or-remove-an-in-place-hold-exchange-2013-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если при подготовке облачного архива для локальных почтовых ящиков используется архивация на базе Exchange Online, хранением на месте необходимо управлять из локальной организации Exchange 2013. Параметры хранения автоматически передаются в облачный архив с помощью DirSync. Как отмечалось выше, вместе с локальным почтовым ящиком на хранение помещается и соответствующий облачный архив.</td>
</tr>
</tbody>
</table>


Во многих организациях уведомление пользователей о включении режима хранения является обязательным. Кроме того, когда почтовый ящик находится на хранении, не требуется приостанавливать действие политик хранения, применяемых к пользователю почтового ящика. Так как сообщения продолжают удаляться как обычно, пользователи могут не замечать, что включен режим хранения. Если в вашей организации уведомление пользователей о включении режима хранения является обязательным, добавьте уведомление в свойство пользователя почтового ящика **Retention Comment** и используйте свойство **RetentionUrl**, чтобы предоставить ссылку на веб-страницу с дополнительной информацией. В Outlook 2010 и более поздних версий уведомление и URL-адрес отображаются в области Backstage. Чтобы добавить эти свойства почтового ящика и управлять ими, используйте командную консоль Exchange.

К началу

## Помещение общедоступных папок на удержание

В Exchange Online вы можете помещать общедоступные папки на удержание с помощью функции удержания на месте. Хранение для судебного разбирательства не поддерживается в общедоступных папках. Создавая удержание на месте, вы можете применить его только ко всем общедоступным папкам в организации. В результате получится удержание на месте, примененное ко всем почтовым ящикам общедоступных папок.

Кроме того, при помещении общедоступных папок на удержание на месте также сохраняются электронные сообщения, связанные с синхронизацией иерархии общедоступных папок. В результате могут быть сохранены тысячи элементов электронной почты, связанных с синхронизацией иерархии. При этом может исчерпаться квота хранилища для папки "Элементы с возможностью восстановления" в почтовых ящиках общедоступных папок. Чтобы избежать этого, можно применить удержание на месте на основе запроса и добавить в поисковый запрос следующую пару `property:value`:

    NOT(subject:HierarchySync*)

В результате все сообщения (связанные с синхронизацией иерархии общедоступных папок), содержащие фразу "HierarchySync" в строке темы, не помещаются на хранение.

## Функции хранения и папка "Элементы с возможностью восстановления"

При хранении на месте и хранении для судебного разбирательства для удержания элементов используется папка корзины. Эта папка заменяет компонент, обычно называемый *корзиной* в предыдущих версиях Exchange. Папка корзины по умолчанию скрыта в Outlook, Outlook Web App и других клиентах электронной почты. Дополнительные сведения см. в разделе [Папка "Элементы для восстановления"](recoverable-items-folder-exchange-2013-help.md).

По умолчанию при удалении сообщения из папки, отличной от папки "Удаленные", сообщение перемещается в папку "Удаленные". Это называется *перемещением*. Когда пользователь *обратимых удалений* элемент (опытный, нажав клавишу SHIFT и Delete) или удаляет элементы из папки Удаленные, то сообщение перемещается в папку корзины, таким образом, исчезает для данного пользователя.

Элементы хранятся в папке элементов для восстановления в течение срока хранения удаленных элементов, настроенного для базы данных почтовых ящиков пользователя. По умолчанию период хранения удаленного элемента в базах данных почтовых ящиков равен 14 дням. Вы также можете настроить квоту хранения для папки корзины. Это позволяет защитить организацию от возможной атаки типа "отказ в обслуживании", проводимой путем быстрого увеличения объема папки корзины и самой базы данных почтовых ящиков. Если к почтовому ящику не применялось хранение на месте или хранение для судебного разбирательства, из папки корзины при превышении квоты предупреждения или срока хранения удаленных элементов будут безвозвратно удаляться элементы в порядке их поступления.

Папка корзины содержит следующие вложенные папки, которые позволяют хранить удаленные элементы в разных расположениях и упрощают хранение на месте и хранение для судебного разбирательства:

  - **Удаления**. В эту вложенную папку перемещаются элементы, удаленные из папки "Удаленные" или обратимо удаленные из других папок. Они видимы пользователю при использовании средства восстановления удаленных элементов в Outlook и Outlook Web App. Элементы находятся в этой папке по умолчанию до истечения периода хранения удаленного элемента, заданного для базы данных почтовых ящиков или почтового ящика.

  - **Очистка**. Сюда перемещаются элементы, удаленные из папки корзины (с помощью средства восстановления удаленных элементов в Outlook или Outlook Web App). Элементы, для которых истек период хранения, заданный для базы данных почтовых ящиков, также перемещаются в эту папку. Элементы в этой папке не будут видимы пользователям, использующим средство восстановления удаленных элементов. Когда помощник по обслуживанию почтовых ящиков обрабатывает почтовый ящик, элементы в папке "Очистка" удаляются из базы данных почтовых ящиков. Когда вы применяете хранение для судебного разбирательства к пользователю почтового ящика, помощник по обслуживанию почтовых ящиков не удаляет элементы из этой папки.

  - **DiscoveryHold**. Если пользователь помещается на удержание на месте, удаленные элементы будут перемещены в эту папку. Когда помощник по обслуживанию почтовых ящиков обрабатывается почтовый ящик, он оценивает сообщений в этой папке. Соответствие элементов на месте сохраняются до тех пор, пока вопрос удержания период удержания заданного в запросе. Если период удержания не указан, неопределенное время или до тех пор, пока пользователь не удаляется из удержания.

  - **Версии**. Когда для пользователя задано хранение на месте или хранение для судебного разбирательства, необходимо защитить элементы почтового ящика от изменения, в том числе незаконного, пользователем или процессом. Для этого используется процесс *копирования при записи*. Когда пользователь или процесс изменяет определенные свойства элемента почтового ящика, копия исходного объекта сохраняется в папке версий, прежде чем изменение будет совершено. Процесс повторяется для последующих изменений. Сообщения, попавшие в папку версий, также индексируются и возвращаются во время обнаружения электронных данных на месте. После удаления сценария хранения помощник по обслуживанию управляемых папок удаляет копии из папки "Версии".

### Свойства, активирующие копирование при записи

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Тип элемента</th>
<th>Свойства, активирующие копирование при записи</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Сообщения (IPM.Note*)</p>
<p>Сообщения (IPM.Post*)</p></td>
<td><ul>
<li><p>Тема</p></li>
<li><p>Текст сообщения</p></li>
<li><p>Вложения</p></li>
<li><p>Отправители и получатели</p></li>
<li><p>Даты отправки и получения</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Элементы, отличные от сообщений</p></td>
<td><p>Любые изменения видимых свойств за исключением следующих:</p>
<ul>
<li><p>Расположение элемента (когда элемент перемещается между папками)</p></li>
<li><p>Изменение состояния элемента (прочитан или не прочитан)</p></li>
<li><p>Изменения тега хранения, примененного к элементу</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Элементы в папке &quot;Черновики&quot; по умолчанию</p></td>
<td><p>Нет (элементы в папке &quot;Черновики&quot;, для которых отменено копирование при записи)</p></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Помощник по восстановлению календаря определяет, что некоторые участники ответили на приглашение на собрание в форме &quot;Принять&quot; или &quot;Под вопросом&quot; и этот элемент отсутствует в календаре участника. Для элементов календаря и элементов с заданным напоминанием функция копирования при записи отключена для свойств ReminderTime и ReminderSignalTime. Изменения этих свойств не фиксируются функцией копирования при записи. Изменения в RSS-каналах не фиксируются функцией копирования при записи.</td>
</tr>
</tbody>
</table>


Хотя папки "DiscoveryHold", "Очистка" и "Версии" не видны пользователям, все элементы в папке корзины индексируются службой поиска Exchange и могут обнаруживаться в процессе локального обнаружения электронных данных. После удаления сценария хранения на месте или хранения для судебного разбирательства, примененного к пользователю почтового ящика, помощник по обслуживанию управляемых папок удаляет элементы из папок DiscoveryHold, "Очистка" и "Версии".

К началу

## Запреты на удаление и квоты почтового ящика

Элементы в папке корзины не учитываются в квоте почтового ящика пользователя. В Exchange папка корзины имеет свою собственную квоту. В случае Exchange значения по умолчанию для свойств почтового ящика *RecoverableItemsWarningQuota* и *RecoverableItemsQuota* равны 20 ГБ и 30 ГБ соответственно. Чтобы изменить эти значения для базы данных почтовых ящиков в Exchange Server 2013, используйте командлет [Set-MailboxDatabase](https://technet.microsoft.com/ru-ru/library/bb123971\(v=exchg.150\)). Чтобы изменить их для отдельных почтовых ящиков, используйте командлет [Set-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123981\(v=exchg.150\)).

Если папка корзины пользователя превышает квоту предупреждения (заданную параметром *RecoverableItemsWarningQuota*), в журнал событий приложений сервера почтовых ящиков заносится событие. Если папка превышает квоту (заданную параметром *RecoverableItemsQuota*), пользователи не смогут очистить папку "Удаленные" или безвозвратно удалять элементы почтового ящика. Функция копирования при записи также не сможет создавать копии изменяемых элементов. Поэтому критически важно отслеживать квоты папки элементов с возможностью восстановления для пользователей почтовых ящиков, помещенных в режим удержания на месте.

В Exchange Online квота для папки элементов для восстановления (в основной почтовый ящик пользователя) автоматически увеличивается до 100 ГБ при постановка почтового ящика на хранение для судебного разбирательства или хранение на месте. Когда квота хранилища для папки элементов для восстановления в основной почтовый ящик почтовых ящиков на удержание почти достиг своего предела, можно выполнить следующие действия:

  - **Включение архивного почтового ящика и включение развертываемым архивации**   Без ограничений емкости для папки восстанавливаемых элементов можно включить путем включения в архивный почтовый ящик и затем Включение архивации компонента, развертываемым в Exchange Online. Это приводит к 100 ГБ для папки элементов для восстановления в основной почтовый ящик и неограниченного емкость хранилища для папки элементов для восстановления в архив пользователя. Просмотреть как: [Enable архивных почтовых ящиков в Office 365 безопасности & центре соответствия требованиям](https://go.microsoft.com/fwlink/p/?linkid=863320) и [Включить неограниченном архивировании в Office 365](https://go.microsoft.com/fwlink/p/?linkid=844569).
    
    **Примечания**.
    
      - После включения архив для почтового ящика, приближается к завершению превышении квоты хранения для папки восстанавливаемых элементов может потребоваться запуск помощника управляемых папок вручную запуск помощника для обработки почтового ящика, чтобы переместить просроченные элементы Папки восстанавливаемых элементов в архивный почтовый ящик. Сведения содержатся в разделе шаг 4 в [Увеличение квот для почтовых ящиков на хранение элементов для восстановления](https://go.microsoft.com/fwlink/p/?linkid=786479).
    
      - Обратите внимание на то, что другие элементы в почтовом ящике пользователя могут быть перемещены в новый архивный почтовый ящик. Рекомендуем после включения архивного почтового ящика сообщить пользователю, что это может произойти.

  - **Создание политики хранения настраиваемых для почтовых ящиков на хранение**    В дополнение к Включение архивного почтового ящика и развертываемым архивации для почтовых ящиков на хранение для судебного разбирательства или хранение на месте, может потребоваться создать политику хранения настраиваемых для почтовых ящиков на удержание. Это давайте можно применить политику хранения к почтовым ящикам на удержание, отличный от политики управления записями сообщений по умолчанию, которая применяется к почтовым ящикам, которых нет на удержание. Это позволяет применять теги хранения, предназначенные специально для почтовых ящиков на удержание. Этот компонент включает создание тега хранения для папки элементов для восстановления.

Дополнительные сведения можно [увеличить квоту для почтовых ящиков на хранение элементов для восстановления](https://go.microsoft.com/fwlink/p/?linkid=786479).

## Запреты на удаление и пересылка электронной почты

Настроить пересылку электронной почты для своего почтового ящика можно с помощью Outlook и Outlook Web App. Пользователи могут настроить пересылку отправляемых им сообщений в другие почтовые ящики в вашей организации или за ее пределами. Пересылку электронной почты можно настроить так, чтобы сообщения, отправляемые в исходный почтовый ящик, не копировались в него, а отправлялись на указанный адрес пересылки.

Если переадресация почты настроена для почтового ящика и сообщения не копируются в исходный почтовый ящик, что произойдет, если почтовый ящик находится на удержании? Поведение отличается на основе того, является ли почтовый ящик в организации Exchange 2013 или Exchange Online.

  - **Exchange Online**    Параметры хранения для почтового ящика проверяются в процессе доставки. Если сообщение соответствует критериям хранения для почтового ящика, копия сообщения сохраняется в папке корзины. Это значит, что пересланные сообщения можно найти в исходном почтовом ящике с помощью функции обнаружения электронных данных на месте.

  - **Exchange 2013**    Если сообщения пересылаются в другой почтовый ящик и не копируются в исходный, они не сохраняются в папке корзины. Это значит, что найти пересланные сообщения с помощью функции обнаружения электронных данных на месте будет невозможно. Чтобы устранить эту проблему, организации Exchange 2013 могут запретить пользователям настраивать пересылку электронной почты.

К началу

## Хранение архивированного содержимого Lync

Exchange 2013, Microsoft Lync 2013 и Microsoft SharePoint 2013 обеспечивают интегрированное сохранение и обнаружение электронных данных, что позволяет хранить и искать элементы в различных хранилищах данных. Exchange 2013 позволяет архивировать контент Lync Server 2013 в Exchange, благодаря чему отсутствует требование о наличии отдельной базы данных SQL Server для хранения архивированного контента Lync. Интегрированная способность удержания и eDiscovery позволяет SharePoint 2013 в сохранения и поиска данных в хранилищах с одной консоли.

Когда вы применяете к почтовому ящику Exchange 2013 хранение на месте или хранение для судебного разбирательства, содержимое Microsoft Lync 2013 (например, мгновенные сообщения и файлы, к которым был предоставлен общий доступ на собрании по сети) архивируется в почтовом ящике. Если поиск eDiscovery почтовых ящиков в центр помощи Microsoft SharePoint 2013 или на месте в eDiscovery Exchange 2013, любые архивные Lync сопоставление контента поисковый запрос, также возвращаются в результатах поиска. Также можно ограничить поиск содержимым ящика хранятся в Lync.

Чтобы включить архивацию содержимого в Lync Exchange 2013 ящика, необходимо настроить Lync 2013 интеграция с Exchange 2013. Дополнительные сведения см. в следующих разделах:

  - [Планирование архивации](https://technet.microsoft.com/ru-ru/library/jj205069\(v=ocs.15\))

  - [Развертывание архивации](https://technet.microsoft.com/ru-ru/library/jj205147\(v=ocs.15\))

К началу

## Удаление почтового ящика на хранении

При удалении почтового ящика, помещенного на хранение для судебного разбирательства или хранение на месте, результат зависит от того, в какой организации находится почтовый ящик: Exchange 2013 или Exchange Online.

  - **Exchange 2013**    Если администратор удаляет учетную запись пользователя, с которой связан почтовый ящик, то банк данных Exchange со временем обнаружит, что почтовый ящик больше не подключен к учетной записи пользователя, и пометит этот почтовый ящик как подлежащий удалению, даже если он находится на хранении. Чтобы сохранить почтовый ящик, сделайте следующее:
    
    1.  Не удаляйте учетную запись пользователя, а отключите ее.
    
    2.  Измените свойства почтового ящика, чтобы ограничить его использование и доступ к нему. Например, установите для квот на отправку и получение значение 1, заблокируйте потенциальных отправителей сообщений на этот почтовый ящик и ограничьте возможность доступа к нему.
    
    3.  Храните почтовый ящик, пока не будут удалены все данные или не исчезнет потребность в их хранении.

  - **Exchange Online**    Если почтовый ящик пользователя помещается на хранение на месте или хранение для судебного разбирательства, а соответствующая учетная запись Office 365 удаляется, почтовый ящик становится *неактивным*, т. е. удаленным с возможностью восстановления. В неактивных почтовых ящиках можно хранить содержимое почтовых ящиков пользователей после их увольнения из организации. Элементы в неактивном почтовом ящике хранятся в течение всего срока хранения, который был задан до того, как ящик стал неактивным. Это позволяет администраторам, сотрудникам, ответственным за обеспечение соответствия требованиям, и сотрудникам, управляющим записями, использовать функцию обнаружения электронных данных на месте для доступа к содержимому неактивного почтового ящика и поиска в нем. Неактивные почтовые ящики не могут получать электронную почту и не отображаются в общей адресной книге организации и других списках. Дополнительные сведения см. в статье [Неактивные почтовые ящики в Exchange Online](https://technet.microsoft.com/ru-ru/library/dn798632\(v=exchg.150\)).

К началу

## Перенос почтовых ящиков на хранении из Exchange 2013 в Office 365

Если у вас гибридное развертывание Exchange, указанные ниже условия выполняются при переносе локального почтового ящика Exchange 2013 в службу Exchange Online в Office 365:

  - Если локальный почтовый ящик помещен на хранение для судебного разбирательства или хранение на месте, параметры хранения сохраняются после переноса почтового ящика в Exchange Online.

  - Если локальный почтовый ящик помещен на хранение для судебного разбирательства или хранение на месте, все содержимое папки корзины перемещается в почтовый ящик Exchange Online.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Параметры хранения и содержимое папки корзины также сохраняются при переносе почтового ящика Exchange Online в локальную организацию Exchange 2013.</td>
</tr>
</tbody>
</table>


Существуют и другие способы переноса локальных данных электронной почты в Office 365, например поэтапная или прямая миграция Exchange.

  - Поэтапную миграцию можно использовать для переноса почтовых ящиков из Exchange 2003 или Exchange 2007 в Office 365. В этих версиях Exchange папка "Элементы с возможностью восстановления" (и ее функции) не существует. Поэтому при переносе почтовых ящиков Exchange 2003 или Exchange 2007 в Office 365 нет содержимого папки "Элементы с возможностью восстановления" для перемещения.

  - Прямая миграция используется для переноса почтовых ящиков из Exchange 2003, Exchange 2007 и Exchange 2010 в Office 365. Как отмечалось выше, в почтовых ящиках Exchange 2003 и Exchange 2007 папка корзины отсутствует. Так как эта папка появилась в Exchange 2010, при прямой миграции почтовых ящиков Exchange 2010 ее содержимое переносится в Office 365.

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для переноса локальных почтовых ящиков в Office 365 из Exchange 2013 и Exchange 2010 рекомендуем использовать гибридное развертывание Exchange.</td>
</tr>
</tbody>
</table>


К началу
