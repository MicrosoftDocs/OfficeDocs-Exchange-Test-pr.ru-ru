﻿---
title: 'Справка по Exchange 2013: отсутствие в сайте или домене хозяина схемы'
TOCTitle: Отсутствует в сайте/домене хозяина схемы_NotInSchemaMasterSite
ms:assetid: 3aafd22a-d0f0-4120-a325-886fb2eb43ef
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.notinschemamastersite(v=EXCHG.150)
ms:contentKeyID: 50487852
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Отсутствует в сайте/домене хозяина схемы\_NotInSchemaMasterSite

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Установку Microsoft® Exchange Server 2007 не удается продолжить, так как компьютер, на котором выполняется установка, расположен не в том же сайте или домене службы каталогов Active Directory®, что и сервер с ролью хозяина схемы домена, также известной как FSMO.

Для установки Exchange 2007 необходимо, чтобы контроллер домена, функционирующий как хозяин схемы домена, был в том же сайте и домене, что и локальный компьютер, на котором выполняется установка Exchange.

Хозяин схемы домена управляет всеми обновлениями и изменениями схемы Active Directory.

Чтобы устранить эту проблему, выполните установку Exchange Server 2007 с использованием параметров **/prepareschema** и **/prepareAD** в сайте и домене, в которых расположен хозяин схемы домена.

Дополнительные сведения о параметрах командной **строки/prepareschemaи/PrepareAD** приведены в разделе документации по Exchange 2007 продукта «Как для подготовки Active Directory и домены» (<https://go.microsoft.com/fwlink/?linkid=78453>)

Чтобы определить роль, можно использовать средство хозяина схемы. Однако, чтобы сделать средство схемы доступным в виде оснастки консоли MMC, необходимо зарегистрировать DLL-библиотеку Schmmgmt.dll.

Просмотр текущего хозяина схемы

1.  В командной строке введите **regsvr32 schmmgmt.dll**
    
    > [!NOTE]  
    > Регистрация <strong>RegSvr32</strong> будет успешно выполнена, если появится следующее диалоговое окно:<br />
    Успешная регистрация DllRegisterServer в schmmgmt.dll.


2.  Чтобы открыть новую консоль управления, нажмите кнопку **Пуск**, щелкните **Выполнить**, а затем введите **mmc**.

3.  В меню консоли выберите команду **Добавить или удалить оснастку**.

4.  Нажмите кнопку **Добавить**, чтобы открыть диалоговое окно **Добавить изолированную оснастку**.

5.  Выберите **Схема Active Directory** и нажмите кнопку **Добавить**.

6.  Появится диалоговое окно добавления оснастки "Схема Active Directory". Щелкните **Закрыть** и нажмите кнопку **ОК**, чтобы вернуться в консоль.

7.  Выберите **Схема Active Directory**. В области справа отобразятся разделы **Классы** и **Атрибуты**.

8.  Щелкните правой кнопкой мыши **Схема Active Directory** и выберите **Хозяин операций**.

9.  На экране отобразится текущий хозяин схемы.

После определения текущего хозяина схемы определите подсеть, в которой он расположен. Затем установите Exchange одним из приведенных ниже способов:

  - Измените подсеть сервера Exchange, чтобы переместить его в сайт, в котором расположен хозяин схемы. Затем установите Exchange.

  - Временно измените принадлежность сервера Exchange к сайту и установите Exchange. После установки Exchange верните сервер в исходный сайт.

Принудительное изменение принадлежности к сайту

1.  Запустите редактор реестра на том сервере, где хотите установить Exchange. Для этого нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **regedit** и нажмите кнопку **ОК**.

2.  Перейдите к следующему подразделу реестра:
    
    **HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\Netlogon\\Parameters**

3.  Создайте следующий параметр новой **Строки**:
    
    Имя параметра: **SiteName**
    
    Тип значения: **REG\_SZ**
    
    Значение: **\<site\_that\_contains\_the\_schema\_master\>**

4.  Закройте редактор реестра и перезапустите службу входа в сеть. После выполнения этого действия сервер Exchange станет участником указанного вами сайта.

5.  Установите Exchange.

6.  Удалите значение реестра, которое вы добавили на шаге 3.

7.  Перезапустите службу входа в сеть. Это действие вернет принадлежность сервера Exchange к исходному сайту.

