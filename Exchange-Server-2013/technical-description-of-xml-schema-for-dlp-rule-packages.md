---
title: 'Разработка пакетов правил конфиденциальной информации: Exchange 2013 Help'
TOCTitle: Разработка пакетов правил конфиденциальной информации
ms:assetid: c4ab8707-0839-4855-9390-3dbcb43475a7
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ674704(v=EXCHG.150)
ms:contentKeyID: 50489050
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Разработка пакетов правил конфиденциальной информации

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2016-07-28_

Схема XML и руководство в этом разделе помогут создать собственные основные XML-файлы для защиты от утечки данных, определяющие для вас типы конфиденциальной информации в пакете правила классификации. После создания XML-файла правильного формата вы сможете импортировать его с помощью Центра администрирования Exchange или командной консоли Exchange, чтобы создать решения для защиты от утечки данных Microsoft Exchange Server 2013. XML-файл, который представляет собой настраиваемый шаблон политики защиты от утечки данных, может содержать символы XML, которые являются вашим пакетом правила классификации. Для просмотра сведений об определении собственных шаблонов DLP в качестве XML-файлов см. раздел [Определение собственных шаблонов DLP и типов сведений](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md).

**Содержание**

Обзор процесса создания и настройки правил

Описание правила

Базовая структура правила

Использование местных языков в XML-файле

Определение пакета правила классификации схемы XML

Дополнительные сведения

## Обзор процесса создания и настройки правил

Процесс создания и настройки правил включает следующие общие этапы.

1.  Подготовка набора документов для тестирования, представляющих целевую среду. К важным ключевым характеристикам набора документов для тестирования относятся: набор документов включает сущность или сходство, для которых создается правило, и набор документов не включает сущность или сходство, для которых создается правило.

2.  Определение правил, соответствующих требованиям утверждения (точность и эффективность), для идентификации подходящего содержимого. Для этого может потребоваться развитие нескольких условий в пределах правила, связанных логикой, которые удовлетворяют минимальным требованиям соответствия для определения целевых документов.

3.  Установка рекомендуемого уровня вероятности для правил на основе требований утверждения (точность и эффективность). Рекомендуемый уровень вероятности может считаться уровнем вероятности для правила по умолчанию.

4.  Проверка правил с помощью создания экземпляра политики с правилами и отслеживания образца содержимого для тестирования. Отрегулируйте правила или уровень вероятности на основе результатов, чтобы максимально увеличить количество обнаруженного содержимого и, в то же время, уменьшить количество ложных положительных и негативных результатов. Продолжайте проверку и настраивание правил, пока не достигните удовлетворительного уровня обнаружения содержимого для позитивных и негативных образцов.

Сведения о схеме XML для файлов шаблона политики см. в разделе [Разработка файлов шаблонов политики DLP](xml-rule-schema-and-rule-structure-guide-for-dlp-policy-files.md).

## Описание правила

Для механизма обнаружения конфиденциальной информации для политики защиты от утечки данных можно создать правила двух типов: Сущность и сходство. Выбранный тип правила базируется на типе логики обработки, который следует применить при обработке содержимого, как описано в предыдущих разделах. Определения правил настраиваются в XML-документах в формате, описанном с помощью стандартизированных правил XSD. В этих правилах описан тип содержимого, которому необходимо соответствовать, и уровень вероятности, что упомянутое соответствие представляет собой целевое содержимое. Уровень вероятности указывает на возможность появления сущности, если в содержимом найден шаблон, или на возможность сходства, если в содержимом присутствует свидетельство.

## Базовая структура правила

Определение правила состоит из трех основных компонентов:

1.  **Сущность**   определяет логику сопоставления и подсчета для этого правила

2.  **Сходство**   определяет логику соответствия для этого правила

3.  **Локализованные строки**   локализация имен правил и их описаний

Дополнительно используются три поддерживающих элемента, которые определяют подробности обработки и которые упоминаются среди основных компонентов: ключевое слово, регулярное выражение и функция. С использованием ссылок в нескольких правилах сущности и сходства может использоваться одно определение поддерживающих элементов, например номер социального обеспечения. Базовая структура правила в XML-формате выглядит следующим образом.

    <?xml version="1.0" encoding="utf-8"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
    
      <RulePack id="DAD86A92-AB18-43BB-AB35-96F7C594ADAA">
        <Version major="1" minor="0" build="0" revision="0"/>
        <Publisher id="619DD8C3-7B80-4998-A312-4DF0402BAC04"/>
        <Details defaultLangCode="en-us">
          <LocalizedDetails langcode="en-us">
            <PublisherName>DLP by EPG</PublisherName>
            <Name>CSO Custom Rule Pack</Name>
            <Description>This is a rule package for a EPG demo.</Description>
          </LocalizedDetails>
        </Details>
      </RulePack>
    
      <Rules>
    
        <!-- Employee ID -->
        <Entity id="E1CC861E-3FE9-4A58-82DF-4BD259EAB378" patternsProximity="300" recommendedConfidence="75">
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Regex_employee_id" />
            <Match idRef="Keyword_employee" />
          </Pattern>
        </Entity>
    
        <Regex id="Regex_employee_id">(\s)(\d{9})(\s)</Regex>
        <Keyword id="Keyword_employee">
          <Group matchStyle="word">
            <Term>Identification</Term>
            <Term>Contoso Employee</Term>
          </Group>
        </Keyword>
    
    
        <LocalizedStrings>
    
          <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB378">
            <Name default="true" langcode="en-us">
              Employee ID
            </Name>
            <Description default="true" langcode="en-us">
              A custom classification for detecting Employee ID's
            </Description>
          </Resource>
    
        </LocalizedStrings>
      </Rules>
    </RulePackage>

## Правила сущности

Правила сущности нацелены на четко определенные идентификаторы, такие как номер социального обеспечения, и представлены коллекцией исчисляемых шаблонов. Правила сущности возвращают число значений и уровень вероятности соответствия, где "число значений" — это общее число обнаруженных экземпляров сущности, а "уровень вероятности" — возможность, что данная сущность существует в этом документе. Сущность содержит атрибут "id" в качестве уникального идентификатора. Идентификатор используется для локализации, управления версиями и выполнения запросов. Идентификатор сущности должен быть глобальным уникальным идентификатором и не должен дублироваться в других сущностях или сходствах. Об этом упоминается в разделе о локализированных строках.

Правила сущности содержат необязательный атрибут patternsProximity (по умолчанию = 300), используемый при применении логики, чтобы указать соседство нескольких шаблонов для удовлетворения условий соответствия. Элемент "Сущность" включает один или несколько дочерних элементов шаблона, и каждый шаблон является индивидуальной репрезентацией сущности, например сущность кредитной карты или водительского удостоверения. В шаблоне имеется требуемый атрибут confidenceLevel, который представляет точность шаблона на основе набора данных образца. В шаблоне может быть три дочерних элемента:

1.  IdMatch — он является обязательным.

2.  Match

3.  Любой

Если любой из элементов шаблона возвратит значение "True", шаблон будет выполнен. Подсчет элементов сущности равен суме всех обнаруженных подсчетов шаблона.

![Математическая формула для счетчика объектов](images/JJ674704.25309939-98bc-4460-8f89-8560bbad7981(EXCHG.150).gif "Математическая формула для счетчика объектов")

где k — количество элементов шаблона для сущности.

Шаблон должен иметь только один элемент IdMatch. Элемент IdMatch представляет идентификатор, с которым должен совпасть шаблон, например, номер кредитной карты или индивидуальный идентификационный номер налогоплательщика. Подсчет для шаблона — количество элементов IdMatch, которые совпали с элементом шаблона. Элемент IdMatch привязывает окно близости к элементам Match.

Другой необязательный дочерний элемент шаблона — элемент Match, представляющий подтверждающее свидетельство, которое должно соответствовать для поиска элемента IdMatch. Например, для правила с наивысшим уровнем вероятности может потребоваться, чтобы в дополнение к номеру кредитной карты в документе, в окне близости кредитной карты, существовали дополнительные артефакты, такие как адрес и имя. Эти дополнительные артефакты отображаются в элементах Match или Any (эти элементы подробно описаны в разделе "Методы и способы соответствия"). Несколько элементов Match могут содержаться в определении шаблона, который может быть включен непосредственно в элемент шаблона или объединен с помощью элемента Any для определения семантики соответствия. Если в окне близости найдено соответствие, привязанное к содержимому IdMatch, возвращается значение True.

Элементы IdMatch и Match не определяют, какое содержимое должно соответствовать, но ссылаются на него с помощью атрибута idRef. Это способствует повторному использованию определений в нескольких конструкциях шаблона.

    <Entity id="..." patternsProximity="300" > 
        <Pattern confidenceLevel="85">
            <IdMatch idRef="FormattedSSN" />
            <Any minMatches="1">
                <Match idRef="SSNKeyword" />
                <Match idRef="USDate" />
                <Match idRef="USAddress" />
                <Match idRef="Name" />
            </Any>
        </Pattern>  
        <Pattern confidenceLevel="65">
            <IdMatch idRef="UnformattedSSN" />
            <Match idRef="SSNKeyword" />
            <Any minMatches="1">        
                <Match idRef="USDate" />
                <Match idRef="USAddress" />
                <Match idRef="Name" />
            </Any>
        </Pattern>
    </Entity> 

Элемент id сущности, представленный в предыдущем XML-документе с помощью "…", должен быть идентификатором GUID. Этот элемент описан в разделе "Локализованные строки".

## Окно близости шаблона сущности

Сущность содержит необязательное значение атрибута patternsProximity (целое число, по умолчанию = 300), используемое для поиска шаблонов. Для каждого шаблона значение атрибута определяет расстояние (в символах Unicode) от расположения элемента IdMatch до всех других элементов Match, заданных для этого шаблона. Окно близости с помощью расположения элемента IdMatch привязывается к окну по левую и правую сторону элемента IdMatch.

![Текстовый шаблон с отозванными соответствующими элементами](images/JJ674704.65d52989-f50f-4097-b39a-9612f860d727(EXCHG.150).gif "Текстовый шаблон с отозванными соответствующими элементами")

В следующем примере показано влияние окна близости на алгоритм соответствия, где для элемента IdMatch страхового номера требуется как минимум одно из подтверждающих соответствий адреса, имени или даты. Только элементы SSN1 и SSN4 соответствуют, поскольку для элементов SSN2 и SSN3 в окне близости не найдено ни одного подтверждающего свидетельство или найдено, но частичное.

![Примеры срабатывания и несрабатывания правила вероятности](images/JJ674704.8117deb3-d8c8-4d4e-a011-ac5f9990b08e(EXCHG.150).gif "Примеры срабатывания и несрабатывания правила вероятности")

Обратите внимание, что текст сообщения и каждое вложение считаются независимыми элементами. Это означает, что окно близости не выходит за их границы. Элемент idMatch и подкрепляющие доказательства для каждого элемента (вложения или основного текста) должны оставаться внутри них.

## Уровень вероятности сущности

Уровень вероятности элемента сущности является комбинацией всех уровней вероятности выполненного шаблона. Они объединяются с помощью указанной ниже формулы.

![Математическая формула вероятности объектов](images/JJ674704.9b8bb9c8-3ded-4ea5-a609-71d8034b1017(EXCHG.150).gif "Математическая формула вероятности объектов")

где k — количество элементов шаблона для сущности, а несоответствующий шаблон возвращает уровень вероятности, равен 0.

Возвращаясь к примеру образца кода структуры элемента сущности, если оба шаблона соответствуют, уровень вероятности сущности равен 94,75 % на основе указанных ниже вычислений:

CLСущность= 1 – \[(1 – CLШаблон1) x (1 – CLШаблон1)\]

*= 1 – \[(1 – 0,85) x (1 – 0,65)\]*

*= 1 – (0,15 x 0,35)*

*= 94.75%*

Аналогично, если соответствует только второй шаблон, уровень вероятности сущности равен 65 % на основе следующих вычислений:

CLСущность= 1 – \[(1 – CLШаблон1) X (1 – CLШаблон1)\]

*= 1 – \[(1 – 0) X (1 – 0,65)\]*

*= 1 – (1 X 0,35)*

*= 65%*

Эти значения вероятности в правилах назначены отдельным шаблонам на основе набора тестовых документов, проверенных в качестве части процесса создания правила.

## Правила сходства

Правила сходства нацелены на содержимое без четких идентификаторов, например, закон Сарбейна-Оксли или корпоративное финансовое содержимое. Для этого содержимого невозможно найти один подходящий идентификатор, а вместо этого для анализа требуется определить, имеет ли место сбор свидетельств. Правила сходства не возвращают подсчет, вместо этого они возвращают, если найдено, соотнесенный уровень вероятности. Содержимое сходства представлено в качестве коллекции независимых свидетельств. Свидетельством является совокупность необходимых соответствий в пределах определенной близости. Для правила сходства близость определяется атрибутом evidencesProximity (600 по умолчанию), а минимальный уровень вероятности — атрибутом thresholdConfidenceLevel.

Правила сходства имеют атрибут id для уникального идентификатора, используемого для локализации, управления версиями и выполнения запросов. Поскольку правила сходства не зависят от четких идентификаторов, они, в отличие от правил сущности, не содержат элемент IdMatch.

Каждое правило сходства имеет один или несколько дочерних элементов Evidence, определяющих свидетельство, которое необходимо найти, и уровень вероятности, способствующий выполнению правила сходства. Сходство не считается найденным, если итоговый уровень вероятности находится ниже порогового значения. Каждый элемент Evidence логически представляет собой подтверждающее свидетельство для этого "типа" документа, а атрибут confidenceLevel уточняет этот элемент Evidence в наборе данных для тестирования.

Элементы Evidence имеют один или несколько дочерних элементов Match или Any. Если соответствуют все дочерние элементы Match и Any, элемент Evidence находится и уровень вероятности способствует вычислению уровня вероятности правил. Описание для правила сущности применимо и к элементам Match и Any относительно правил сходства.

    <Affinity id="..." 
              evidencesProximity="1000"
              thresholdConfidenceLevel="65">
        <Evidence confidenceLevel="40">
            <Any> 
                <Match idRef="AssetsTerms" /> 
                <Match idRef="BalanceSheetTerms" /> 
                <Match idRef="ProfitAndLossTerms" /> 
            </Any> 
        </Evidence>
        <Evidence confidenceLevel="40">
            <Any minMatches="2"> 
                <Match idRef="TaxTerms" /> 
                <Match idRef="DollarAmountTerms" /> 
                <Match idRef="SECTerms" /> 
                <Match idRef="SECFilingFormTerms" /> 
                <Match idRef="DollarTotalRegex" /> 
            </Any> 
        </Evidence>
    </Affinity>

## Окно близости сходства

Расчет окна близости для сходства отличается от расчета шаблонов сущности. Близость сходства соответствует модели скользящего окна. Алгоритм близости сходства пытается найти в данном меню максимальное количество свидетельств. Уровень вероятности элемента Evidence в окне близости должен быть выше порогового значения, определенного для правила сходства, которое необходимо найти.

![Текст рядом с примером срабатывания правила определения сходства](images/JJ674704.2601ec86-0094-43fa-8d22-9d97f7465942(EXCHG.150).gif "Текст рядом с примером срабатывания правила определения сходства")

## Уровень вероятности сходства

Уровень вероятности для сходства равен сумме найденных элементов Evidence в окне близости для правила сходства. Хотя он аналогичен уровню вероятности правила сущности, главное различие состоит в применении окна близости. Аналогично правилам сущности, уровень вероятности элемента сходства является суммой всех выполненных уровней вероятности элемента Evidence, но для правила сходства он показывает только наибольшую комбинацию элементов Evidence, найденную в пределах окна близости. Уровни вероятности элементов Evidence суммируются с помощью указанной ниже формулы.

![Математическая формула вероятности правила определения сходства](images/JJ674704.8a5da4ca-af02-4c5a-ab60-0072dc7e7a0f(EXCHG.150).gif "Математическая формула вероятности правила определения сходства")

где k — количество элементов Evidence для сходства, соответствующего в пределах окна близости.

Возвращаясь к примеру структуры правила сходства на рис.4, если все три свидетельства соответствуют в пределах скользящего окна близости, уровень вероятности сходства равен 85,6 % на основе следующих расчетов. Это число превышает пороговое значение для правила сходства — 65, что вызывает соответствие правил.

CLСходство= 1 – \[(1 – CLСвидетельство 1) X (1 – CLСвидетельство 2) X (1 – CLСвидетельство 2)\]

*= 1 – \[(1 – 0,6) X (1 – 0,4) X (1 – 0,4)\]*

*= 1 – (0,4 X 0,6 X 0,6)*

*= 85.6%*

![Пример срабатывания правила определения сходства с высоким уровнем вероятности](images/JJ674704.e17b2e22-18c3-40c4-8f19-0993bb556675(EXCHG.150).gif "Пример срабатывания правила определения сходства с высоким уровнем вероятности")

Используя то же самое определение правила, если только первое свидетельство соответствует, поскольку второе свидетельство находится за пределами окна близости, максимальный уровень вероятности сходства равен 60 % на основе расчетов, указанных ниже, и правило сходства не соответствует, поскольку пороговое значение 65 не достигнуто.

CLСходство= 1 – \[(1 – CLСвидетельство 1) X (1 – CLСвидетельство 2) X (1 – CLСвидетельство 2)\]

*= 1 – \[(1 – 0,6) X (1 – 0) X (1 – 0)\]*

*= 1 – (0,4 X 1 X 1)*

*= 60%*

![Пример срабатывания правила определения сходства с низким уровнем вероятности](images/JJ674704.077095b1-6eb0-40df-b254-f33437725720(EXCHG.150).gif "Пример срабатывания правила определения сходства с низким уровнем вероятности")

## Настраивание уровней вероятности

Один из главных аспектов процесса создания правила состоит в настраивании уровней вероятности для правил сущности и сходства. После создания определений правила примените правило к образцу содержимого и соберите точные данные. Сравните возвращенные результаты для каждого шаблона или свидетельства с ожидаемыми результатами для документа для тестирования.

![Сравнительная таблица с примерами срабатывания правила](images/JJ674704.25a7d9a1-d02f-447e-a88b-8e78bdc0413a(EXCHG.150).gif "Сравнительная таблица с примерами срабатывания правила")

Если правила соответствуют требованиям утверждения, то есть, если уровень вероятности шаблона или свидетельства выше установленного порогового значения (например, 75 %), то выражение соответствия завершено и можно переходить к следующему этапу.

Если шаблон или свидетельство не соответствуют уровню вероятности, необходимо его повторно создать (например, добавив больше подтверждающих свидетельств, удалив или добавив дополнительные шаблоны или свидетельства, и др.) и повторить это действие.

Далее необходимо настроить уровень вероятности для каждого шаблона или свидетельства правила на основании результатов предыдущего этапа. Для каждого шаблона или свидетельства подсчитайте количество истинных положительных результатов (подмножество документов, содержащих сущность или сходство для которых создается правило и которые возникают в результате соответствия) и количество ложных положительных результатов (подмножество документов, не содержащих сущность или сходство, для которых создается правило, но которые так же вернули соответствие). Уровень вероятности для каждого шаблона или свидетельства настраивается с помощью следующих расчетов:

*Уровень вероятности = истинные положительные / (истинные положительные + ложные положительные)*


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Шаблон или свидетельство</th>
<th>Истинные положительные</th>
<th>Ложные положительные</th>
<th>Уровень вероятности</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>P1или E1</p></td>
<td><p>4</p></td>
<td><p>1</p></td>
<td><p>80%</p></td>
</tr>
<tr class="even">
<td><p>P2или E2</p></td>
<td><p>2</p></td>
<td><p>2</p></td>
<td><p>50%</p></td>
</tr>
<tr class="odd">
<td><p>Pnили En</p></td>
<td><p>9</p></td>
<td><p>10</p></td>
<td><p>47%</p></td>
</tr>
</tbody>
</table>


## Использование местных языков в XML-файле

Схема правила поддерживает сохранение локализованных имен и описание для каждого элемента сущности и сходства. Каждый элемент сущности или сходства должен иметь соответствующий элемент в разделе "Локализованные строки". Для локализации каждого элемента включите элемент ресурса в качестве дочернего элемента LocalizedStrings, чтобы сохранить имя и описания нескольких языковых стандартов для каждого элемента. Элемент источника включает требуемый атрибут idRef, совпадающий с соответствующим атрибутом idRef для каждого локализуемого элемента. Дочерние элементы языкового стандарта элемента источника имеют локализованные имя и описания для каждого указанного языкового стандарта.

    <LocalizedStrings>
        <Resource idRef="guid">
            <Locale langcode="en-US" default="true"> 
                <Name>affinity name en-us</Name> 
                <Description>
                    affinity description en-us
                </Description> 
            </Locale> 
            <Locale langcode="de"> 
                <Name>affinity name de</Name> 
                <Description>
                    affinity description de
                </Description> 
            </Locale> 
        </Resource>
    </LocalizedStrings>

## Определение пакета правила классификации схемы XML

    <?xml version="1.0" encoding="utf-8"?>
    <xs:schema xmlns:mce="http://schemas.microsoft.com/office/2011/mce"
               targetNamespace="http://schemas.microsoft.com/office/2011/mce" 
               xmlns:xs="http://www.w3.org/2001/XMLSchema"
               elementFormDefault="qualified"
               attributeFormDefault="unqualified"
               id="RulePackageSchema">
      <xs:simpleType name="LangType">
        <xs:union memberTypes="xs:language">
          <xs:simpleType>
            <xs:restriction base="xs:string">
              <xs:enumeration value=""/>
            </xs:restriction>
          </xs:simpleType>
        </xs:union>
      </xs:simpleType>
      <xs:simpleType name="GuidType" final="#all">
        <xs:restriction base="xs:token">
          <xs:pattern value="[0-9a-fA-F]{8}\-([0-9a-fA-F]{4}\-){3}[0-9a-fA-F]{12}"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:complexType name="RulePackageType">
        <xs:sequence>
          <xs:element name="RulePack" type="mce:RulePackType"/>
          <xs:element name="Rules" type="mce:RulesType">
            <xs:key name="UniqueRuleId">
              <xs:selector xpath="mce:Entity|mce:Affinity"/>
              <xs:field xpath="@id"/>
            </xs:key>
            <xs:key name="UniqueProcessorId">
              <xs:selector xpath="mce:Regex|mce:Keyword"></xs:selector>
              <xs:field xpath="@id"/>
            </xs:key>
            <xs:key name="UniqueResourceIdRef">
              <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
              <xs:field xpath="@idRef"/>
            </xs:key>        
            <xs:keyref name="ReferencedRuleMustExist" refer="mce:UniqueRuleId">
              <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
              <xs:field xpath="@idRef"/>
            </xs:keyref>
            <xs:keyref name="RuleMustHaveResource" refer="mce:UniqueResourceIdRef">
              <xs:selector xpath="mce:Entity|mce:Affinity"/>
              <xs:field xpath="@id"/>
            </xs:keyref>
          </xs:element>
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="RulePackType">
        <xs:sequence>
          <xs:element name="Version" type="mce:VersionType"/>
          <xs:element name="Publisher" type="mce:PublisherType"/>
          <xs:element name="Details" type="mce:DetailsType">
            <xs:key name="UniqueLangCodeInLocalizedDetails">
              <xs:selector xpath="mce:LocalizedDetails"/>
              <xs:field xpath="@langcode"/>
            </xs:key>
            <xs:keyref name="DefaultLangCodeMustExist" refer="mce:UniqueLangCodeInLocalizedDetails">
              <xs:selector xpath="."/>
              <xs:field xpath="@defaultLangCode"/>
            </xs:keyref>
          </xs:element>
          <xs:element name="Encryption" type="mce:EncryptionType" minOccurs="0" maxOccurs="1"/>
        </xs:sequence>
        <xs:attribute name="id" type="mce:GuidType" use="required"/>
      </xs:complexType>
      <xs:complexType name="VersionType">
        <xs:attribute name="major" type="xs:unsignedShort" use="required"/>
        <xs:attribute name="minor" type="xs:unsignedShort" use="required"/>
        <xs:attribute name="build" type="xs:unsignedShort" use="required"/>
        <xs:attribute name="revision" type="xs:unsignedShort" use="required"/>
      </xs:complexType>
      <xs:complexType name="PublisherType">
        <xs:attribute name="id" type="mce:GuidType" use="required"/>
      </xs:complexType>
      <xs:complexType name="LocalizedDetailsType">
        <xs:sequence>
          <xs:element name="PublisherName" type="mce:NameType"/>
          <xs:element name="Name" type="mce:RulePackNameType"/>
          <xs:element name="Description" type="mce:OptionalNameType"/>
        </xs:sequence>
        <xs:attribute name="langcode" type="mce:LangType" use="required"/>
      </xs:complexType>
      <xs:complexType name="DetailsType">
        <xs:sequence>
          <xs:element name="LocalizedDetails" type="mce:LocalizedDetailsType" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="defaultLangCode" type="mce:LangType" use="required"/>
      </xs:complexType>
      <xs:complexType name="EncryptionType">
        <xs:sequence>
          <xs:element name="Key" type="xs:normalizedString"/>
          <xs:element name="IV" type="xs:normalizedString"/>
        </xs:sequence>
      </xs:complexType>
      <xs:simpleType name="RulePackNameType">
        <xs:restriction base="xs:token">
          <xs:minLength value="1"/>
          <xs:maxLength value="64"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="NameType">
        <xs:restriction base="xs:normalizedString">
          <xs:minLength value="1"/>
          <xs:maxLength value="256"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="OptionalNameType">
        <xs:restriction base="xs:normalizedString">
          <xs:minLength value="0"/>
          <xs:maxLength value="256"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="RestrictedTermType">
        <xs:restriction base="xs:string">
          <xs:minLength value="1"/>
          <xs:maxLength value="512"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:complexType name="RulesType">
        <xs:sequence>
          <xs:choice maxOccurs="unbounded">
            <xs:element name="Entity" type="mce:EntityType"/>
            <xs:element name="Affinity" type="mce:AffinityType"/>
          </xs:choice>
          <xs:choice minOccurs="0" maxOccurs="unbounded">
            <xs:element name="Regex" type="mce:RegexType"/>
            <xs:element name="Keyword" type="mce:KeywordType"/>
          </xs:choice>
          <xs:element name="LocalizedStrings" type="mce:LocalizedStringsType"/>
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="EntityType">
        <xs:sequence>
          <xs:element name="Pattern" type="mce:PatternType" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="id" type="mce:GuidType" use="required"/>
        <xs:attribute name="patternsProximity" type="mce:ProximityType" use="required"/>
        <xs:attribute name="recommendedConfidence" type="mce:ProbabilityType"/>
        <xs:attribute name="workload" type="mce:WorkloadType"/>
      </xs:complexType>
      <xs:complexType name="PatternType">
        <xs:sequence>
          <xs:element name="IdMatch" type="mce:IdMatchType"/>
          <xs:choice minOccurs="0" maxOccurs="unbounded">
            <xs:element name="Match" type="mce:MatchType"/>
            <xs:element name="Any" type="mce:AnyType"/>
          </xs:choice>
        </xs:sequence>
        <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
      </xs:complexType>
      <xs:complexType name="AffinityType">
        <xs:sequence>
          <xs:element name="Evidence" type="mce:EvidenceType" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="id" type="mce:GuidType" use="required"/>
        <xs:attribute name="evidencesProximity" type="mce:ProximityType" use="required"/>
        <xs:attribute name="thresholdConfidenceLevel" type="mce:ProbabilityType" use="required"/>
        <xs:attribute name="workload" type="mce:WorkloadType"/>
      </xs:complexType>
      <xs:complexType name="EvidenceType">
        <xs:sequence>
          <xs:choice maxOccurs="unbounded">
            <xs:element name="Match" type="mce:MatchType"/>
            <xs:element name="Any" type="mce:AnyType"/>
          </xs:choice>
        </xs:sequence>
        <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
      </xs:complexType>
      <xs:complexType name="IdMatchType">
        <xs:attribute name="idRef" type="xs:string" use="required"/>
      </xs:complexType>
      <xs:complexType name="MatchType">
        <xs:attribute name="idRef" type="xs:string" use="required"/>
      </xs:complexType>
      <xs:complexType name="AnyType">
        <xs:sequence>
          <xs:choice maxOccurs="unbounded">
            <xs:element name="Match" type="mce:MatchType"/>
            <xs:element name="Any" type="mce:AnyType"/>
          </xs:choice>
        </xs:sequence>
        <xs:attribute name="minMatches" type="xs:nonNegativeInteger" default="1"/>
        <xs:attribute name="maxMatches" type="xs:nonNegativeInteger" use="optional"/>
      </xs:complexType>
      <xs:simpleType name="ProximityType">
        <xs:restriction base="xs:positiveInteger">
          <xs:minInclusive value="1"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="ProbabilityType">
        <xs:restriction base="xs:integer">
          <xs:minInclusive value="1"/>
          <xs:maxInclusive value="100"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="WorkloadType">
        <xs:restriction base="xs:string">
          <xs:enumeration value="Exchange"/>
          <xs:enumeration value="Outlook"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:complexType name="RegexType">
        <xs:simpleContent>
          <xs:extension base="xs:string">
            <xs:attribute name="id" type="xs:token" use="required"/>
          </xs:extension>
        </xs:simpleContent>
      </xs:complexType>
      <xs:complexType name="KeywordType">
        <xs:sequence>
          <xs:element name="Group" type="mce:GroupType" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="id" type="xs:token" use="required"/>
      </xs:complexType>
      <xs:complexType name="GroupType">
        <xs:sequence>
          <xs:choice>
            <xs:element name="Term" type="mce:TermType" maxOccurs="unbounded"/>
          </xs:choice>
        </xs:sequence>
        <xs:attribute name="matchStyle" default="word">
          <xs:simpleType>
            <xs:restriction base="xs:NMTOKEN">
              <xs:enumeration value="word"/>
              <xs:enumeration value="string"/>
            </xs:restriction>
          </xs:simpleType>
        </xs:attribute>
      </xs:complexType>
      <xs:complexType name="TermType">
        <xs:simpleContent>
          <xs:extension base="mce:RestrictedTermType">
            <xs:attribute name="caseSensitive" type="xs:boolean" default="false"/>
          </xs:extension>
        </xs:simpleContent>
      </xs:complexType>
      <xs:complexType name="LocalizedStringsType">
        <xs:sequence>
          <xs:element name="Resource" type="mce:ResourceType" maxOccurs="unbounded">
            <xs:key name="UniqueLangCodeUsedInNamePerResource">
              <xs:selector xpath="mce:Name"/>
              <xs:field xpath="@langcode"/>
            </xs:key>
            <xs:key name="UniqueLangCodeUsedInDescriptionPerResource">
              <xs:selector xpath="mce:Description"/>
              <xs:field xpath="@langcode"/>
            </xs:key>
          </xs:element>
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="ResourceType">
        <xs:sequence>
          <xs:element name="Name" type="mce:ResourceNameType" maxOccurs="unbounded"/>
          <xs:element name="Description" type="mce:DescriptionType" minOccurs="0" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="idRef" type="mce:GuidType" use="required"/>
      </xs:complexType>
      <xs:complexType name="ResourceNameType">
        <xs:simpleContent>
          <xs:extension base="xs:string">
            <xs:attribute name="default" type="xs:boolean" default="false"/>
            <xs:attribute name="langcode" type="mce:LangType" use="required"/>
          </xs:extension>
        </xs:simpleContent>
      </xs:complexType>
      <xs:complexType name="DescriptionType">
        <xs:simpleContent>
          <xs:extension base="xs:string">
            <xs:attribute name="default" type="xs:boolean" default="false"/>
            <xs:attribute name="langcode" type="mce:LangType" use="required"/>
          </xs:extension>
        </xs:simpleContent>
      </xs:complexType>
    </xs:schema>

## Дополнительные сведения

[Защита от потери данных](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Определение собственных шаблонов DLP и типов сведений](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md)

