---
title: 'Удаление политики адресной книги: Exchange 2013 Help'
TOCTitle: Удаление политики адресной книги
ms:assetid: c20c6f82-2f75-4116-9be1-c5af10113f71
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Hh529946(v=EXCHG.150)
ms:contentKeyID: 50489035
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Удаление политики адресной книги

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2014-03-25_

Используйте эту процедуру для удаления политики адресной книги.

Дополнительные сведения об управленческих задачах, связанных с политиками адресных книг, см. в разделе [Процедуры политики адресной книги](address-book-policy-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения: менее 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Политики адресных книг" в разделе [Разрешения для электронных адресов и адресных книг](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Политику адресной книги невозможно удалить, если она назначена почтовому ящику пользователя или обратимо удаленному почтовому ящику. Чтобы определить, назначена ли политика адресной книги пользователю, выполните в командной строке следующую команду:
    
    `Get-Mailbox | Where $._AddressBookPolicy -eq <AddressBookPolicyName>`
    
    Чтобы определить, назначена ли политика адресной книги обратимо удаленному почтовому ящику, выполните приведенную ниже команду.
    
    `Get-Mailbox -SoftDeletedMailbox | Where $._AddressBookPolicy -eq <AddressBookPolicyName>`

  - Чтобы удалить политику адресной книги из почтового ящика пользователя, можно воспользоваться страницей **Функции почтового ящика** в свойствах почтового ящика или командлетом **Set-Mailbox**.

  - Невозможно использовать Центр администрирования Exchange (EAC) для удаления политики адресной книги. Необходимо использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование командной консоли для удаления политики адресной книги

В этом примере удаляется политика адресной книги с именем ABP\_TailspinToys.

    Remove-AddressBookPolicy -Identity "ABP_TailspinToys"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-AddressBookPolicy](https://technet.microsoft.com/ru-ru/library/hh529929\(v=exchg.150\)).

