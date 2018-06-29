---
title: 'Настройка встроенных типов конфиденциальных сведений DLP: Exchange 2013 Help'
TOCTitle: Настройка встроенных типов конфиденциальных сведений DLP
ms:assetid: 3f8bf141-2e7c-4ea7-b102-dfd6c41539da
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn781122(v=EXCHG.150)
ms:contentKeyID: 62757541
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка встроенных типов конфиденциальных сведений DLP

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2016-05-26_

При поиске конфиденциальных данных в сообщении электронной почте необходимо описать эти данные в *правиле*. Служба защиты от потери данных (DLP) содержит пакет из 51 правила для самых распространенных типов конфиденциальных данных, которые вы можете использовать. Для этого необходимо включить их в политику. Иногда эти встроенные правила требуется скорректировать в соответствии с потребностями организации. Для этого можно создать настраиваемый тип конфиденциальных данных. В этой статье показано, как изменить XML-файл, содержащий существующую коллекцию правил, чтобы обнаружить более широкий круг данных кредитных карт.

Вы можете использовать этот пример для изменения других встроенных типов конфиденциальных данных. Список типов конфиденциальных данных по умолчанию и определений XML см. в статье [Что позволяют искать типы конфиденциальной информации в Exchange](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md).

В этой статье описываются следующие разделы для настройки XML-правил:

  - Экспорт XML-файла с текущими правилами

  - Найдите правило, которое требуется изменить, в XML.

  - Изменение XML и создание типа конфиденциальных данных

  - Удаление требования подкрепляющего свидетельства из типа конфиденциальных данных

  - Поиск ключевых слов, связанных с вашей организацией

  - Отправка правила

Сведения о том, где располагаются различные части правил и за что они отвечают, см. в статье Глоссарий терминов в конце этой статьи.

## Экспорт XML-файла с текущими правилами

Для экспорта XML-файла необходимо использовать Командная консоль Exchange или . В случае Exchange Server 2013 см. статью [Использование Powershell с Exchange 2013 (командная консоль Exchange)](https://technet.microsoft.com/ru-ru/library/bb123778\(v=exchg.150\)). В случае Exchange Online см. статью [Подключение к Exchange Online с помощью удаленной оболочки PowerShell](https://technet.microsoft.com/ru-ru/library/jj984289\(v=exchg.150\)).

1.  В Командная консоль Exchange или Exchange Online PowerShell введите команду **Get-ClassificationRuleCollection**, чтобы отобразить правила организации на экране. Если вы не создавали собственные правила, вы увидите только стандартные, встроенные правила, отмеченные как "Пакет правил Майкрософт".

2.  Сохраните правила организации в переменной, введя команду **$ruleCollections = Get-ClassificationRuleCollection**. Переменные можно затем удобно использовать в командах удаленной оболочки PowerShell.

3.  Создайте форматированный XML-файл со всеми данными, введя команду **Set-Content -path "C:\\custompath\\exportedRules.xml" -Encoding Byte -Value $ruleCollections.SerializedClassificationRuleCollection**. (**Set-content** — это часть командлета, который записывает XML в файл.)
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Убедитесь, что используется расположение, где фактически хранится пакет правил. <strong>C:\custompath\</strong> — это просто замещающий текст.</td>
    </tr>
    </tbody>
    </table>


## Найдите правило, которое требуется изменить, в XML.

Предыдущие командлеты экспортировали всю *коллекцию правил*, состоящую из 51 стандартного правила. После этого вам необходимо найти именно то правило для номера кредитной карты, которое вы хотите изменить.

1.  Откройте в текстовом редакторе XML-файл, экспортированный в предыдущем разделе.

2.  Прокрутите вниз до тега **\<Rules\>**, который представляет начало раздела с правилами DLP. (Этот XML-файл содержит сведения для всей коллекции правил, поэтому необходимо пропустить общие данные в начале файла, чтобы добраться до правил.)

3.  Найдите **Func\_credit\_card** с определением правила для номера кредитной карты. (В XML имена правил не могут содержать пробелы, поэтому они обычно заменяются на подчеркивания. Кроме того, имена правил иногда сокращаются. Например, имя правила для номера социального страхования — "SSN".) XML для правила номера кредитной карты будет выглядеть, как в следующем примере кода.
    
        <Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085"
               patternsProximity="300" recommendedConfidence="85">
              <Pattern confidenceLevel="85">
               <IdMatch idRef="Func_credit_card" />
                <Any minMatches="1">
                  <Match idRef="Keyword_cc_verification" />
                  <Match idRef="Keyword_cc_name" />
                  <Match idRef="Func_expiration_date" />
                </Any>
              </Pattern>
            </Entity>

После того как вы нашли определение правила для номера кредитной карты, вы можете изменить код XML правила в соответствии с вашими потребностями. (Сведения об определениях XML см. в статье Глоссарий терминов в конце этой статьи.)

## Изменение XML и создание типа конфиденциальных данных

Во-первых, вам потребуется создать тип конфиденциальных данных, так как напрямую правила по умолчанию не могут быть изменены. С настраиваемыми типами конфиденциальных данных можно выполнять различные операции, описанные в статьи [Разработка пакетов правил конфиденциальной информации](technical-description-of-xml-schema-for-dlp-rule-packages.md). Для простоты в этом примере мы удалим подкрепляющее свидетельство и добавим ключевые слова в правило номера кредитной карты.

Все XML-определения правил основаны на следующем шаблоне. Вам потребуется скопировать и вставить XML-определение правила номера кредитной карты в шаблон, изменить некоторые значения (обратите внимание на заполнители ". . .” в следующем примере) и загрузить измененный XML как новое правило, которое можно использовать в политиках.

    <?xml version="1.0" encoding="utf-16"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
      <RulePack id=". . .">
        <Version major="1" minor="0" build="0" revision="0" />
        <Publisher id=". . ." /> 
        <Details defaultLangCode=". . .">
          <LocalizedDetails langcode=" . . . ">
             <PublisherName>. . .</PublisherName>
             <Name>. . .</Name>
             <Description>. . .</Description>
          </LocalizedDetails>
        </Details>
      </RulePack>
      
     <Rules>
       <!-- Paste the Credit Card Number rule definition here.--> 
    
          <LocalizedStrings>
             <Resource idRef=". . .">
               <Name default="true" langcode=" . . . ">. . .</Name>
               <Description default="true" langcode=". . ."> . . .</Description>
             </Resource>
          </LocalizedStrings>
    
       </Rules>
    </RulePackage>

Вы получили код, который похож на следующий XML-фрагмент. Так как пакеты правил и правила идентифицируются по уникальным GUID, необходимо создать два GUID: один для пакета правил и один для замены GUID правила номера кредитной карты. (GUID для кода объекта в следующем примере кода — это идентификатор для определения встроенного правила, который необходимо заменить на новый.) GUID можно создать несколькими способами, например ввести в PowerShell команду **\[guid\]::NewGuid()**.

    <?xml version="1.0" encoding="utf-16"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
      <RulePack id="8aac8390-e99f-4487-8d16-7f0cdee8defc">
        <Version major="1" minor="0" build="0" revision="0" />
        <Publisher id="8d34806e-cd65-4178-ba0e-5d7d712e5b66" />
        <Details defaultLangCode="en">
          <LocalizedDetails langcode="en">
            <PublisherName>Contoso Ltd.</PublisherName>
            <Name>Financial Information</Name>
            <Description>Modified versions of the Microsoft rule package</Description>
          </LocalizedDetails>
        </Details>
      </RulePack>
      
     <Rules>
        <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f"
           patternsProximity="300" recommendedConfidence="85">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Func_credit_card" />
            <Any minMatches="1">
              <Match idRef="Keyword_cc_verification" />
              <Match idRef="Keyword_cc_name" />
              <Match idRef="Func_expiration_date" />
            </Any>
          </Pattern>
        </Entity>
    
          <LocalizedStrings>
             <Resource idRef="db80b3da-0056-436e-b0ca-1f4cf7080d1f"> 
    <!-- This is the GUID for the preceding Credit Card Number entity because the following text is for that Entity. -->
               <Name default="true" langcode="en-us">Modified Credit Card Number</Name>
               <Description default="true" langcode="en-us">Credit Card Number that looks for additional keywords, and another version of Credit Card Number that doesn't require keywords (but has a lower confidence level)</Description>
             </Resource>
          </LocalizedStrings>
    
       </Rules>
    </RulePackage>

## Удаление требования подкрепляющего свидетельства из типа конфиденциальных данных

После создания типа конфиденциальных данных, который можно загрузить в среду Exchange, необходимо настроить правило. Измените его так, чтобы оно искало 16-разрядный номер, который передает контрольную сумму, но не требует дополнительных (подкрепляющих) свидетельств (например, ключевых слов). Для этого потребуется удалить часть XML, которая ищет подкрепляющее свидетельство. Подкрепляющие свидетельства помогают сократить число ложных срабатываний, так как обычно они представляют собой определенные ключевые слова или дату истечения срока действия рядом с номером кредитной карты. Если удалить такое свидетельство, также следует снизить уровень вероятности нахождения номера кредитной карты, уменьшив значение **confidenceLevel**, которое в этом примере равно 85.

    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Func_credit_card" />
          </Pattern>
        </Entity>

## Поиск ключевых слов, связанных с вашей организацией

Вам может потребоваться подкрепляющее свидетельство, но с другими или дополнительными ключевыми словами. Также вы можете изменить область поиска этого свидетельства. Вы можете скорректировать **patternsProximity**, чтобы расширить или сузить окно поиска свидетельства возле 16-разрядного номера. Чтобы добавить собственные ключевые слова, необходимо задать список ключевых слов и указать его в правиле. Следующий XML-фрагмент добавляет ключевые слова "company card" (карта компании) и "Contoso card" (карта Contoso), чтобы любое сообщение с этими фразами в пределах 150 символов от номера кредитной карты определялось как номер кредитной карты.

    <Rules>
    <! -- Modify the patternsProximity to be "150" rather than "300." -->
        <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="150" recommendedConfidence="85">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Func_credit_card" />
            <Any minMatches="1">
              <Match idRef="Keyword_cc_verification" />
              <Match idRef="Keyword_cc_name" />
    <!-- Add the following XML, which references the keywords at the end of the XML sample. -->
              <Match idRef="My_Additional_Keywords" />
              <Match idRef="Func_expiration_date" />
            </Any>
          </Pattern>
        </Entity>
    <!-- Add the following XML, and update the information inside the <Term> tags with the keywords that you want to detect. -->
        <Keyword id="My_Additional_Keywords">
          <Group matchStyle="word">
            <Term caseSensitive="false">company card</Term>
            <Term caseSensitive="false">Contoso card</Term>
          </Group>
        </Keyword>

## Отправка правила

Чтобы отправить правило, выполните следующие действия.

1.  Сохраните правило как XML-файл с кодировкой Юникод. Это важно, так как правило в другой кодировке работать не будет.

2.  Подключитесь к Командная консоль Exchange или Exchange Online PowerShell. В случае Exchange Server 2013 см. статью [Использование Powershell с Exchange 2013 (командная консоль Exchange)](https://technet.microsoft.com/ru-ru/library/bb123778\(v=exchg.150\)). В случае Exchange Online см. статью [Подключение к Exchange Online с помощью удаленной оболочки PowerShell](https://technet.microsoft.com/ru-ru/library/jj984289\(v=exchg.150\)).

3.  В Командная консоль Exchange или Exchange Online PowerShell введите команду **New-ClassificationRuleCollection -FileData (Get-Content -Path "C:\\custompath\\MyNewRulePack.xml " -Encoding Byte)**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Убедитесь, что используется расположение, где фактически хранится пакет правил. <strong>C:\custompath\</strong> — это просто замещающий текст.</td>
    </tr>
    </tbody>
    </table>


4.  Для подтверждения введите **Y** и нажмите клавишу **ВВОД**.

5.  Убедитесь, что новое правило загружено, введя команду **Get-DataClassification**, которая покажет имя вашего правила.

Чтобы начать использовать новое правило для обнаружения конфиденциальных данных, необходимо добавить правило в политику DLP. Сведения о добавлении правила в политику см. в статье [Управление политиками защиты от потери данных](manage-dlp-policies-exchange-2013-help.md).

## Глоссарий терминов

Это определения терминов, которые используются в этой процедуре.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Термин</th>
<th>Определение</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Сущность</p></td>
<td><p>Сущности — это то, что мы называем типами конфиденциальных данных, например номера кредитных карт. У каждой сущности есть уникальный идентификатор GUID. Если скопировать GUID и выполнить его поиск, вы найдете XML-определение правила и его локализованный перевод. Это определение также можно найти, выполнив поиск GUID для перевода, а затем выполнив поиск этого GUID.</p></td>
</tr>
<tr class="even">
<td><p>Функции</p></td>
<td><p>В XML-файле указана ссылка на <strong>Func_credit_card</strong> — функцию в скомпилированном коде. Функции используются для выполнения сложных регулярных выражений и проверки соответствия контрольных сумм для встроенных правил. Так как все происходит в коде, некоторые переменные в XML-файле не отображаются.</p></td>
</tr>
<tr class="odd">
<td><p>IdMatch</p></td>
<td><p>Это идентификатор, с которым должен совпасть шаблон, например, номер кредитной карты. Дополнительные сведения об этом элементе и тегах <strong>Match</strong> см. в статье <a href="technical-description-of-xml-schema-for-dlp-rule-packages.md">Entity rules</a>.</p></td>
</tr>
<tr class="even">
<td><p>Списки ключевых слов</p></td>
<td><p>XML-файл также ссылается на <strong>keyword_cc_verification</strong> и <strong>keyword_cc_name</strong>. Это списки ключевых слов, с которыми мы ищем совпадения в элементе <strong>patternsProximity</strong> сущности. Они в XML не отображаются.</p></td>
</tr>
<tr class="odd">
<td><p>Шаблон</p></td>
<td><p>Шаблон содержит список искомых типом конфиденциальных данных сведений. К ним относятся ключевые слова, регулярные выражения и внутренние функции (которые выполняют различные задачи, такие как проверка контрольных сумм). Типы конфиденциальных данных могут использовать несколько шаблонов с уникальными уровнями вероятности. Это полезно при создании типа конфиденциальных данных, который возвращает высокую вероятность, если найдено подкрепляющее свидетельство, и низкий уровень вероятности, если свидетельств мало или они не найдены.</p></td>
</tr>
<tr class="even">
<td><p>Параметр confidenceLevel шаблона</p></td>
<td><p>Это уровень вероятности совпадения, определенный модулем DLP. Он связан с совпадением с шаблоном, если заданы соответствующие требования. Это значение следует учитывать при использовании правил транспорта Exchange (ETR).</p></td>
</tr>
<tr class="odd">
<td><p>patternsProximity</p></td>
<td><p>Если мы нашли что-то похожее на шаблон номера кредитной карты, в <strong>patternsProximity</strong> — области возле этого номера — мы будем искать подкрепляющее свидетельство.</p></td>
</tr>
<tr class="even">
<td><p>recommendedConfidence</p></td>
<td><p>Это рекомендуемый для правила уровень вероятности. Он применяется к сущностям и привязкам. В случае сущностей этот номер никогда не сравнивается со значением <strong>confidenceLevel</strong> для шаблона. Это просто дополнительный фактор, помогающий выбрать уровень вероятности. В случае привязок значение <strong>confidenceLevel</strong> шаблона должно быть больше значения <strong>recommendedConfidence</strong>, чтобы можно было инициировать действие ETR. <strong>recommendedConfidence</strong> — это уровень вероятности по умолчанию, используемый в правилах ETR, при котором вызывается действие. При необходимости можно вручную изменить правило ETR так, чтобы вызывать в зависимости от уровня вероятности шаблона.</p></td>
</tr>
</tbody>
</table>


## Дополнительные сведения

  - [Применение правил защиты от потери данных для оценки сообщений](how-dlp-rules-are-applied-to-evaluate-messages-exchange-2013-help.md)

  - [Создание настраиваемой политики DLP](create-a-custom-dlp-policy-exchange-2013-help.md)

  - [Что позволяют искать типы конфиденциальной информации в Exchange](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md)

