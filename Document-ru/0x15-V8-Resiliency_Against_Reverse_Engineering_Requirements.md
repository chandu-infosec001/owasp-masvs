# V8: Требования устойчивости к внешним воздействиям

## Цель проверки

В этом разделе рассматриваются меры по глубокой эшелонированности защиты, рекомендуемые для приложений, которые обрабатывают или предоставляют доступ к конфиденциальным данным или функциям. Отсутствие какого-либо из этих элементов защиты не приводит к образованию уязвимости - напротив, они призваны повысить устойчивость приложения к обратному проектированию и конкретным атакам на стороне клиента.

Требования в этом разделе должны применяться по мере необходимости, которая основывается на оценке рисков, вызванных несанкционированным вмешательством в приложение и/или обратным проектирование кода. Мы предлагаем обратиться к документу OWASP «Technical Risks of Reverse Engineering and Unauthorized Code Modification Reverse Engineering and Code Modification Prevention» (см. ссылки ниже) для списка бизнес рисков, а также связанных с ними технических угроз.

Для того чтобы любое из требований в приведенном ниже списке было эффективным, приложение должно выполнить, по меньшей мере, все MASVS-L1 (т. е. надежные требования по обеспечению безопасности должны быть соблюдены), а также все требования с более низким номером в V8. Например, требования обфускации, перечисленные в разделе «создание препятсвий для анализа», должны сочетаться с «изоляцией приложения», «препятствование динамическому анализу и изменению» и «привязке устройства».

**Обратите внимание, что защита программного обеспечения никогда не должна использоваться в качестве замены средств контроля безопасности. Требования, перечисленные в MASVR-R, предназначены для добавления специальных средств защиты, завясящих от угрозы, приложения, которое должно соответствовать требованиям безопасности MASVS.**

Следующие предположения необходимо иметь в виду:

1. Должна быть определена модель угроз, в которой они четко прописаны, и от которых происходит защита. Кроме того, должна быть указана степень защиты, которую должна обеспечить схема. Например, заявленная цель может заключаться в том, чтобы заставить авторов вредоносных программ, которые хотят изучить приложение, приложить значительные усилия для осуществления ручного обратного проектирования. 

2. Модель угрозы должна быть предельно ясной. Например, скрытие криптографического ключа в реализации whitebox не имеет смысла, если злоумышленник может просто посмотреть весь код.

3. Эффективность защиты всегда должна проверяться экспертом, имеющим опыт тестирования конкретных типов защиты от фальсификации и обфускации (см. также главы «обратное проектирование» и «оценка защиты программного обеспечения» в OWASP MSTG.

### Создание препятствий для обратного проектирования и фальсификации

| # | Описание | R |
| --- | --- | --- |
| **8.1** | Приложение обнаруживает и реагирует на наличие root или jailbreak либо путем уведомления пользователя, либо прекращением работы приложения. | ✓ |
| **8.2** | Приложение не позволяет использовать отладчики и/или обнаруживает и реагирует на использование отладчика. Все доступные отладочные протоколы должны быть учтены. | ✓ |
| **8.3** | Приложение обнаруживает и реагирует на подмену исполняемых файлов и критических данных в своей песочнице. | ✓ |
| **8.4** | Приложение обнаруживает и реагирует на наличие широко используемых инструментов и фреймворков обратного проектирования на устройстве.| ✓ |
| **8.5** | Приложение обнаруживает и реагирует на запуск в эмуляторе.  | ✓ |
| **8.6** | Приложение обнаруживает и реагирует на фальсификацию кода и данных в своем собственном пространстве памяти. | ✓ |
| **8.7** | Приложение реализует несколько механизмов в каждой категории защиты (с 8.1 по 8.6). Обратите внимание, что на отказоустойчивость влияет количество и разнообразие оригинальности используемых механизмов. | ✓ |
| **8.8** | Механизмы обнаружения инициируют ответы разных типов, включая отложенные и скрытые ответы. | ✓ |
| **8.9** | Обфускация применяется к программной защите, которая, в свою очередь, препятствует деобфускации посредством динамического анализа.  | ✓ |

### Привязка устройства

| # | Описание | R |
| --- | --- | --- |
| **8.10** | Приложение реализует функциональность привязки устройства, используя отпечаток устройства, полученный из нескольких свойств, уникальных для устройства. | ✓ |

### Создание препятсвий для анализа

| # | Описание | R |
| --- | --- | --- |
| **8.11** |Все исполняемые файлы и библиотеки, принадлежащие приложению, зашифрованы на уровне файла, и/или важные сегменты кода и данных внутри исполняемых файлов зашифрованы или упакованы. Тривиальный статический анализ не показывает важный код или данные. | ✓ |
| **8.12** | Если целью обфускации является защита конфиденциальных вычислений, используется схема обфускации, которая подходит как для конкретной задачи, так и надежна против ручных и автоматизированных методов деобфускации, учитывая опубликованные в настоящее время исследования. Эффективность схемы обфускации должна быть проверена с помощью ручного тестирования. Обратите внимание, что изоляция аппаратных функций предпочтительнее по сравнению с обфускацией, если это возможно. | ✓ |

## Ссылки

OWASP MSTG содержит подробные инструкции по проверке требований, перечисленных в этом разделе.

- Android - https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05j-Testing-Resiliency-Against-Reverse-Engineering.md
- iOS - https://github.com/OWASP/owasp-mstg/blob/master/Document/0x06j-Testing-Resiliency-Against-Reverse-Engineering.md

Для получения дополнительной информации смотрите также:

- OWASP Mobile Top 10: M8 - Code Tampering, M9 - Reverse Engineering
- WASP Reverse Engineering Threats -https://www.owasp.org/index.php/Technical_Risks_of_Reverse_Engineering_and_Unauthorized_Code_Modification
- OWASP Reverse Engineering and Code Modification Prevention - https://www.owasp.org/index.php/OWASP_Reverse_Engineering_and_Code_Modification_Prevention_Project