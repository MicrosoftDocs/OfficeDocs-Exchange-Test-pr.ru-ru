---
title: Образец схемы XML правила и структуры правила для файлов политики DLP
TOCTitle: Разработка файлов шаблонов политики DLP
ms:assetid: 4b263547-aef4-4ee8-aa4f-fa64a5863189
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ674703(v=EXCHG.150)
ms:contentKeyID: 50488013
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Разработка файлов шаблонов политики DLP

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

В этом обзоре подробно рассматриваются компоненты определения схемы XML для файлов шаблонов политик предотвращения потери данных, а также приведен пример файла политики ML-формата. Перед началом полезно добиться понимания всей архитектуры DLP и принципов разработки правил. Дополнительные сведения см. в разделах [Защита от потери данных](technical-overview-of-dlp-data-loss-prevention-in-exchange.md) и [Определение собственных шаблонов DLP и типов сведений](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md).

Для обеспечения простоты принятия и управления в DLP-решениях в Microsoft Exchange Server 2013 внедряется концептуальная модель политик и шаблонов политик DLP. Шаблоны политик DLP содержат предварительные версии политики DLP. Чтобы быть полезным, шаблон политики DLP должен инкапсулировать все директивы и объекты данных, которые требуются для достижения определенной цели политики, такой как норматив или бизнес-потребность. Шаблон не привязан к определенной среде. Это просто определение или модель политики, которая может быть предоставлена в конфигурации продукта или независимыми поставщиками программного обеспечения и партнерами. С другой стороны, политики DLP — это экземпляры шаблонов время выполнения, привязанные к среде развертывания. Существующая структура политики обмена сообщениями может включать политики DLP с помощью правил транспорта. Правила транспорта предоставляют гибкие средства адаптации и выражают всю мощь DLP-решения.

## Источники и структура шаблона политики

Обычно шаблоны политики DLP создаются на основе разных источников, таких как серверные директивы обработки, клиентские политики компьютера или другие программные конструкции, как показано на следующем рисунке:

![Факторы, влияющие на шаблоны политики](images/JJ674703.12f48e4f-d7b8-4ddd-87e8-8477983252ec(EXCHG.150).gif "Факторы, влияющие на шаблоны политики")

Для шаблонов политики DLP доступны простые операции управления в командной консоли Exchange и интернет-интерфейсах, таких как Центр администрирования Exchange — они включают импорт, экспорт, удаление и средства создания запросов. Политика DLP создается путем указания шаблона политики DLP. Такие шаблоны политики DLP могут быть установлены в системе и храниться в доменных службах Active Directory, либо браться непосредственно из поставляемых извне политик.

Шаблоны политики DLP — это XML-документы. Единая схема XML используется для политик внутри и вне Exchange. Концептуальная структура XML-документа представлена в таблице ниже, где приведены основные элементы. Набор определений компонентов политики помогает достичь конкретной цели, например соблюдения норматива или бизнес-потребности.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Структурный элемент</th>
<th>Значение или пример</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Издатель</p></td>
<td><p>Майкрософт или партнер</p></td>
</tr>
<tr class="even">
<td><p>Version</p></td>
<td><p>15.0.1.0</p></td>
</tr>
<tr class="odd">
<td><p>Имя политики</p></td>
<td><p>PCI-DSS</p></td>
</tr>
<tr class="even">
<td><p>Описание</p></td>
<td><p>Политика DLP PCI-DSS помогает обнаруживать присутствие информации, подпадающей под стандарт защиты данных PCI (PCI DSS), например номера кредитных или дебетовых карт. Использование этой политики не гарантирует соблюдение каких-либо правил. После тестирования внесите требуемые изменения в конфигурацию Exchange, чтобы передача информации соответствовала политике вашей организации. Например, возможно, вам потребуется настроить протокол TLS с известными деловыми партнерами или добавить дополнительные ограничения действия правил транспорта, такие как добавление полномочий для защиты сообщений, содержащих определенный тип данных.</p></td>
</tr>
<tr class="odd">
<td><p>Метаданные</p></td>
<td><p>Теги для описания местных законов, страны или региона, ключевых слов и многого другого.</p></td>
</tr>
<tr class="even">
<td><p>Набор конструкций политики</p></td>
<td><ol>
<li><p>Определения правил транспорта, такие как условия и действия.</p></li>
<li><p>Определение поведения почтового клиента для работы с клиентами через интерактивные уведомления.</p></li>
<li><p>Дополнительные ссылки на конфигурацию, которые должны координироваться со специфическими параметрами клиентской среды.</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>Набор классификаций данных</p></td>
<td><ol>
<li><p>Определяет объекты или сходства классификации.</p></li>
<li><p>Объекты имеют число и вероятность; сходства — только вероятность.</p></li>
<li><p>Содержит собственный набор свойств и схему классификации.</p></li>
</ol></td>
</tr>
</tbody>
</table>


## Определение формата шаблона политики

Шаблоны политики DLP выражаются в XML-документах, которые соответствуют следующей схеме. Обратите внимание на то, что в XML-документе учитывается регистр. Например, `dlpPolicyTemplates` сработает, а `DlpPolicyTemplates` не сработает.

    <?xml version="1.0" encoding="UTF-8"?>
    <dlpPolicyTemplates>
      <dlpPolicyTemplate id="F7C29AEC-A52D-4502-9670-141424A83FAB" mode="Audit" state="Enabled" version="15.0.2.0">
        <contentVersion>4</contentVersion>
        <publisherName>Microsoft</publisherName>
        <name>
          <localizedString lang="en">PCI-DSS</localizedString>
        </name>
        <description>
          <localizedString lang="en">Detects the presence of information subject to Payment Card Industry Data Security Standard (PCI-DSS) compliance requirements.</localizedString>
        </description>
        <keywords></keywords>
        <ruleParameters></ruleParameters>
        <ruleParameters/>
        <policyCommands>
          <!-- The contents below are applied/executed as rules directly in PS - -->
          <commandBlock>
            <![CDATA[ new-transportRule "PCI-DSS: Monitor Payment Card Information Sent To Outside" -DlpPolicy "%%DlpPolicyName%%" -SentToScope NotInOrganization -SetAuditSeverity High -MessageContainsDataClassifications @{Name="Credit Card Number"; MinCount="1" } -Comments "Monitors payment card information sent to outside the organization as part of the PCI-DSS DLP Policy."]]>
          </commandBlock>
          <commandBlock>
            <![CDATA[ new-transportRule "PCI-DSS: Monitor Payment Card Information Sent To Within" -DlpPolicy "%%DlpPolicyName%%" -Comments "Monitors payment card information sent inside the organization as part of the PCI-DSS DLP Policy." -SentToScope InOrganization -SetAuditSeverity Low -MessageContainsDataClassifications @{Name="Credit Card Number"; MinCount="1" } ]]>
          </commandBlock>
        </policyCommands>
        <policyCommandsResources></policyCommandsResources>
      </dlpPolicyTemplate>
    </dlpPolicyTemplates>

Если параметр, который вы включаете в XML-файл для любого элемента, содержит пробел, параметр необходимо заключить в двойные кавычки, иначе он не будет работать надлежащим образом. В приведенном ниже примере параметр, который следует за `-SentToScope`, является допустимым и не включает двойные кавычки, поскольку представляет собой одну непрерывную строку символов без пробела. Однако параметр, предоставленный для –`Comments`, не отобразится в Центре администрирования Exchange, поскольку не заключен в двойные кавычки и содержит пробелы.

    <CommandBlock><![CDATA[ new-transportRule "PCI-DSS: Monitor Payment Card Information Sent To Within" -DlpPolicy "PCI-DSS" -Comments Monitors payment card information sent inside the organization -SentToScope InOrganization -SetAuditSeverity Low -MessageContainsDataClassifications @{Name="Credit Card Number"; MinCount="1" } ]]> </CommandBlock>

## Элемент localizedString

Формат шаблона позволяет локализовать строки в шаблоне, которые могут быть представлены конечным пользователям, например в процессе выбора устанавливаемых шаблонов политик DLP. Этот элемент может использоваться для предоставления различных определений полей Name и Description.

## Узел ruleParameters

Это необязательный набор параметров, которые должны передаваться при создании экземпляра шаблона в ходе создания политики DLP для сопоставления объектов, привязанных к развертыванию. Например, это может быть фактическая группа рассылки, которая будет доступна в развернутой системе.

## Элемент dlpPolicyTemplate

Это корневой элемент для шаблона политики DLP, обязательный для каждого шаблона. Доступные атрибуты показаны в таблице ниже:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя атрибута</th>
<th>Required?</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Версия</p></td>
<td><p>Да</p></td>
<td><p>Номер версии, используемой в документе шаблона политики DLP.</p></td>
</tr>
<tr class="even">
<td><p>State</p></td>
<td><p>Нет</p></td>
<td><p>Необязательная конфигурация по умолчанию для состояния политики.</p></td>
</tr>
<tr class="odd">
<td><p>Mode</p></td>
<td><p>Нет</p></td>
<td><p>Необязательная конфигурация по умолчанию для режима политики.</p></td>
</tr>
<tr class="even">
<td><p>Id</p></td>
<td><p>Нет</p></td>
<td><p>GUID для уникальной идентификации данного определения шаблона политики DLP в следующем формате: &quot;A29C69BF-4F98-47F1-9A99-5771DFD2C27F&quot;.</p></td>
</tr>
</tbody>
</table>


Дочерние элементы включают следующую последовательность элементов.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Дочерний элемент</th>
<th>(минимум, максимум)</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PublisherName</p></td>
<td><p>(1, 1)</p></td>
<td><p>Метаданные для издателя шаблона</p></td>
</tr>
<tr class="even">
<td><p>Name</p></td>
<td><p>(1, 1)</p></td>
<td><p>Локализуемое имя для данного шаблона.</p></td>
</tr>
<tr class="odd">
<td><p>Описание</p></td>
<td><p>(1, 1)</p></td>
<td><p>Локализуемое описание для данного шаблона.</p></td>
</tr>
<tr class="even">
<td><p>Keywords</p></td>
<td><p>(1, 1)</p></td>
<td><p>Список ключевых слов, которые относятся к этому шаблону. Шаблон может содержать пустой список ключевых слов.</p></td>
</tr>
<tr class="odd">
<td><p>RuleParameters</p></td>
<td><p>(0, 1)</p></td>
<td><p>Список параметров шаблона, которые используются в определении политики.</p></td>
</tr>
<tr class="even">
<td><p>PolicyCommands</p></td>
<td><p>(0, 1)</p></td>
<td><p>Список определений правил транспорта для этой политики. Этот элемент является необязательным.</p></td>
</tr>
</tbody>
</table>


## Шаблон политики DLP Управление политикой

Это часть шаблона политики содержит список команд командной консоли Exchange, которые используются для создания экземпляра определения политики. Процесс импорта будет выполнять все команды в рамках процесса создания экземпляра. Ниже приведены примеры команд политики.

    <PolicyCommands>
        <!-- The contents below are applied/executed as rules directly in PS - -->
          <CommandBlock> <![CDATA[ new-transportRule "PCI-DSS: Monitor Payment Card Information Sent To Outside" -DlpPolicy "PCI-DSS" -SentToScope NotInOrganization -SetAuditSeverity High -MessageContainsDataClassifications @{Name="Credit Card Number"; MinCount="1" } -Comments "Monitors payment card information sent to outside the organization as part of the PCI-DSS DLP policy."]]></CommandBlock>
          <CommandBlock><![CDATA[ new-transportRule "PCI-DSS: Monitor Payment Card Information Sent To Within" -DlpPolicy "PCI-DSS" -Comments "Monitors payment card information sent inside the organization as part of the PCI-DSS DLP policy." -SentToScope InOrganization -SetAuditSeverity Low -MessageContainsDataClassifications @{Name="Credit Card Number"; MinCount="1" } ]]> </CommandBlock>
      </PolicyCommands> 

Формат командлетов — стандартный синтаксис командлетов командной консоли Exchange. Команды выполняются по порядку. Каждый из узлов команд может содержать блок сценария, в который войдут несколько команд. Ниже приведен пример, в котором показано, как включить пакет правил классификации внутри шаблона политики DLP и установить пакет правил при создании политики. Пакет правил классификации встраивается в шаблон политики, а затем передается командлету в шаблоне в качестве параметра:

``` 
<CommandBlock>
  <![CDATA[
$rulePack = [system.Text.Encoding]::Unicode.GetBytes('<?xml version="1.0" encoding="utf-16"?>
<rulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">

  <RulePack id="c3f021a3-c265-4dc2-b3a7-41a1800bf518">
    <Version major="1" minor="0" build="0" revision="0"/>
    <Publisher id="e17451d3-9648-4117-a0b1-493a6d5c73ad"/>
    <Details defaultLangCode="en-us">
      <LocalizedDetails langcode="en-us">
        <PublisherName>Contoso</PublisherName>
        <Name>Contoso Sample Rule Pack</Name>
        <Description>This is a sample rule package</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

  <Rules>
    <Entity id="7cc35258-6b35-4415-baff-a76d1a018980" patternsProximity="300" recommendedConfidence="85" workload="Exchange">     

      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_Contoso" />
        <Any minMatches="1">
          <Match idRef="Regex_conf" />
        </Any>
      </Pattern>
    </Entity>

    <Regex id="Regex_Contoso">(?i)(\bContoso\b)</Regex>
    <Regex id="Regex_conf">(?i)(\bConfidential\b)</Regex>

    <LocalizedStrings>
      <Resource idRef="7cc35258-6b35-4415-baff-a76d1a018980">
        <Name default="true" langcode="en-us">
          Confidential Information Rule
        </Name>
        <Description default="true" langcode="en-us">
          Sample rule pack - Detects Contoso confidential information
        </Description>
      </Resource>
    </LocalizedStrings>
  </Rules>

</RulePackage>

')


New-ClassificationRuleCollection -FileData $rulePack 
New-TransportRule -name "customEntity" -DlpPolicy "%%DlpPolicyName%%" -SentToScope NotInOrganization -MessageContainsDataClassifications @{Name="Confidential Information Rule"} -SetAuditSeverity High]]>
</CommandBlock> 
```

Дочерние элементы включают следующую упорядоченную последовательность элементов.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Дочерний элемент</th>
<th>(минимум, максимум)</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CommandBlock</p></td>
<td><p>(1, n)</p></td>
<td><p>Командный блок, который выполняется в PowerShell. Командные блоки выполняются по порядку.</p></td>
</tr>
</tbody>
</table>


## Дополнительные сведения

[Защита от потери данных](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Определение собственных шаблонов DLP и типов сведений](define-your-own-dlp-templates-and-information-types-exchange-2013-help.md)

[Импорт настраиваемого шаблона политики защиты от потери данных из файла](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md)

