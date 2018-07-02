---
title: 'Настройка коллекции виртуальных сертификатов для проверки S/MIME: Exchange 2013 Help'
TOCTitle: Настройка коллекции виртуальных сертификатов для проверки S/MIME
ms:assetid: 04a616e6-197c-490c-ae8c-c8d5f0f0b3dd
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn626155(v=EXCHG.150)
ms:contentKeyID: 61212696
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка коллекции виртуальных сертификатов для проверки S/MIME

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Администратору клиента потребуется настроить коллекцию виртуальных сертификатов, которая будет использоваться для проверки сертификатов S/MIME. Эта коллекция виртуальных сертификатов настраивается как тип файла хранилища сертификатов с расширением имени файла SST. SST-файл содержит все корневые и промежуточные сертификаты, которые используются при проверке сертификата S/MIME.

## Создание и сохранение SST-файла

Для выполнения этой процедуры можно использовать только командную консоль.Сведения о том, как открыть командную консоль Exchange в локальной организации Exchange, см. в статье [Открытие командной консоли Exchange](https://technet.microsoft.com/ru-ru/library/dd638134\(v=exchg.150\)).Сведения о том, как с помощью Оболочка Windows PowerShell подключаться к Exchange Online, см. в статье [Подключение к PowerShell для Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=396554).

Администратор может создать этот SST-файл, экспортировав сертификаты с доверенного компьютера с помощью командлета `Export-Certificate` и указав тип SST. Дополнительные сведения о командлете `Export-Certificate` см. в справочной статье [Export-Certificate](https://technet.microsoft.com/ru-ru/library/hh848628.aspx).

После создания SST-файла используйте командлет `Set-Smimeconfig`, чтобы сохранить его в хранилище виртуальных сертификатов с использованием параметра *-SMIMECertificateIssuingCA*. Например: `Set-SmimeConfig -SMIMECertificateIssuingCA (Get-Content filename.sst -Encoding Byte)`

## Проверка действительности сертификата

Exchange 2013 с пакетом обновления 1 (SP1) сначала проверяет SST-файл, а затем — сертификат. При неудачной проверке сертификат будет проверен путем поиска в хранилище сертификатов на локальном компьютере. Это поведение — нововведение в Exchange 2013 с пакетом обновления 1 (SP1), которое отличается от предыдущих версий Exchange. В Exchange Online для проверки используется только SST.

## Дополнительные сведения

[S/MIME для подписи и шифрования сообщений](s-mime-for-message-signing-and-encryption-exchange-2013-help.md)

[Get-SmimeConfig](https://technet.microsoft.com/ru-ru/library/dn554257\(v=exchg.150\))

