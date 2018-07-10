---
title: 'Наследование списка управления доступом (ACL) заблокировано_InhBlockPublicFolderTree: Exchange 2013 Help'
TOCTitle: Наследование списка управления доступом (ACL) заблокировано_InhBlockPublicFolderTree
ms:assetid: e3b89c8a-d6f8-4864-8bf0-35a78ce87cc4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.inhblockpublicfoldertree(v=EXCHG.150)
ms:contentKeyID: 50489264
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Наследование списка управления доступом (ACL) заблокировано\_InhBlockPublicFolderTree

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2015-03-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Невозможно продолжить установку Microsoft Exchange Server 2007 или Exchange Server 2010, поскольку не удалось распространить требуемые разрешения.

Программе установки Exchange требуется, чтобы для ее объектов, указанных ниже, было включено наследование разрешений.

  - Объект организации Exchange

  - Объект административной группы Exchange

  - Объект контейнера серверов Exchange

  - Объект списка адресов Exchange

  - Объект общедоступной папки Exchange

  - Объект дерева общедоступных папок Exchange

Если не включить наследование разрешений для этих объектов, могут возникнуть проблемы с потоком обработки почты, подключением хранилищ и перерывам в работе службы по другим причинам.

Чтобы устранить эту проблему, включите параметр "Переносить наследуемые от родительского объекта разрешения на этот объект и все его дочерние объекты", а затем повторно запустите программу установки Exchange Server 2007 или Exchange 2010.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Включение наследования разрешений для объекта конфигурации Exchange с помощью диспетчера сервера Exchange Server 2003</p></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Активизируйте вкладку <strong>Безопасность</strong> окна свойств объекта в диспетчере Exchange, настроив соответствующий параметр реестра.</p>
<ol>
<li><p>Запустите редактор реестра (Regedt32.exe).</p></li>
<li><p>Найдите в реестре следующий раздел:</p>
<p><strong>HKEY_CURRENT_USER\Software\Microsoft\Exchange\EXAdmin</strong></p></li>
<li><p>В меню <strong>Правка</strong> щелкните пункт <strong>Создать</strong>, а затем добавьте значение реестра, указанное ниже.</p>
<p><strong>Имя параметра</strong>: ShowSecurityPage</p>
<p><strong>Тип данных</strong>: REG_DWORD</p>
<p><strong>Система счисления</strong>: двоичная</p>
<p><strong>Значение</strong> : 1</p></li>
<li><p>Закройте редактор реестра.</p></li>
</ol>

> [!NOTE]  
> По умолчанию вкладка <strong>Безопасность</strong> не активизирована в окне свойств объекта конфигурации. 

</li>
<li><p>Откройте диспетчер Exchange, найдите требуемый объект, щелкните его правой кнопкой мыши и выберите пункт <strong>Свойства</strong>.</p></li>
<li><p>Откройте вкладку <strong>Безопасность</strong> и щелкните элемент <strong>Дополнительно</strong>.</p></li>
<li><p>Установите флажок <strong>Переносить наследуемые от родительского объекта разрешения на этот объект и все его дочерние объекты</strong>, чтобы включить наследование разрешений.</p></li>
<li><p>Перезапустите сервер Exchange Server.</p></li>
</ol></td>
</tr>
</tbody>
</table>


> [!CAUTION]  
> Неправильное изменение атрибутов объектов Active Directory с помощью редактора ADSI, средства LDP или другого клиента LDAP версии 3 может привести к серьезным неполадкам. В результате может потребоваться переустановка Microsoft Windows Server™ 2003, Exchange Server или обоих продуктов. Изменять атрибуты объектов Active Directory следует с крайней осторожностью. 



<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Повторное включение наследования разрешений для объекта конфигурации Exchange с помощью редактора ADSI в Exchange Server 2007 или Exchange Server 2010</p></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Установите редактор ADSI.</p></li>
<li><p>Запустите редактор ADSI. Нажмите кнопку <strong>Пуск</strong>, выберите команду <strong>Выполнить</strong>, введите в текстовом поле команду <strong>adsiedit.msc</strong> и нажмите кнопку ОК.</p></li>
<li><p>Перейдите к требуемому объекту, щелкните его правой кнопкой мыши и выберите пункт <strong>Свойства</strong>.</p></li>
<li><p>Откройте вкладку <strong>Безопасность</strong> и щелкните элемент <strong>Дополнительно</strong>.</p></li>
<li><p>Установите флажок <strong>Переносить наследуемые от родительского объекта разрешения на этот объект и все его дочерние объекты</strong>, чтобы включить наследование разрешений.</p></li>
<li><p>Чтобы применить изменения, дважды нажмите кнопку <strong>ОК</strong>.</p></li>
<li><p>Дождитесь распространения изменений с помощью репликации Active Directory или выполните принудительную репликацию Active Directory в соответствии с процедурой, описанной в статье 232072 базы знаний Майкрософт &quot;Запуск репликации между непосредственными партнерами репликации Active Directory&quot; (<a href="http://go.microsoft.com/fwlink/?linkid=3052&kbid=232072" class="uri">http://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=232072</a>).</p></li>
</ol></td>
</tr>
</tbody>
</table>

