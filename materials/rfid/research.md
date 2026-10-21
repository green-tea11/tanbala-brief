# UHF RFID простым языком — материалы для сайта VenMart

> Черновик для копирайтера. Каждый факт — со ссылкой. Где источник один или спорный — помечено **⚠ проверить**.
> Собрано: 21.10.2026.

---

## 1. Что такое UHF RFID — в двух словах

**Коротко:** это метка-наклейка с крошечным чипом и антенной. Ридер «зовёт» радиоволной — метка отвечает своим номером. Батарейки в метке нет: энергию она берёт из волны ридера. [Impinj: RFID vs Barcodes](https://www.impinj.com/library/blog/rfid-vs-barcodes-pros-cons-and-how-they-work-together)

- UHF RFID ещё называют **RAIN RFID** — это одно и то же семейство технологий. [Impinj: UHF RFID vs RAIN RFID](https://www.impinj.com/library/blog/uhf-rfid-vs-rain-rfid-the-differences-and-similarities)
- Пассивные UHF-метки обычно читаются на несколько метров; в особых случаях — до ~15 м. Но «типичной» дальности нет — всё зависит от метки и условий (см. раздел 5). [GS1: read range](https://support.gs1.org/support/solutions/articles/43000734166-what-is-the-read-range-for-a-typical-rfid-tag)

### Чем отличается от штрихкода и QR

| | Штрихкод / QR | UHF RFID |
|---|---|---|
| Нужно ли видеть код | Да, сканер должен «увидеть» код | Нет, читает через коробку/упаковку |
| Сколько за раз | По одному | Сотни в секунду (до ~1000/с по данным Impinj) |
| Номер | Часто один на весь артикул | Уникальный у каждой метки |
| Если повреждён | Не читается | Можно подстраховаться печатным штрихкодом на той же этикетке |

Источник: [Impinj: RFID vs Barcodes](https://www.impinj.com/library/blog/rfid-vs-barcodes-pros-cons-and-how-they-work-together). Технологии часто используют **вместе** — на RFID-этикетке печатают и штрихкод (там же).

**Пример для сайта:** «Штрихкод — это как читать книгу по одной странице. RFID — как пролистать всю полку за секунду, не снимая книги».

### Чем отличается от NFC / HF

- **NFC** работает «вплотную» — обычно около 5 см, одна метка за раз. Это про оплату телефоном, билеты, проверку подлинности. [Impinj: NFC vs RAIN RFID](https://www.impinj.com/library/blog/nfc-vs-rfid-and-rain-rfid-differences-and-similarities)
- **UHF (RAIN)** — метры, сотни меток сразу. Это про склад, учёт товаров и имущества, логистику. (там же)
- HF/LF-метки в целом читаются до ~1 м; для платежей и доступа — несколько сантиметров. [GS1: read range](https://support.gs1.org/support/solutions/articles/43000734166-what-is-the-read-range-for-a-typical-rfid-tag)

**Простая формула:** NFC — «приложи», UHF — «пронеси мимо».

---

## 2. Как устроена метка

**Inlay (инлей)** — «сердце» метки: чип + антенна на тонкой плёнке. [atlasRFIDstore: tag, label, inlay](https://www.atlasrfidstore.com/rfid-insider/a-tag-a-label-an-inlay)

- **Dry inlay** — инлей без клея.
- **Wet inlay** — инлей с клеевым слоем, клеится как наклейка.
- **Этикетка (label)** — инлей внутри бумаги/плёнки, на которой можно печатать.
- **Hard tag** — инлей в пластиковом корпусе.

Все четыре определения: [atlasRFIDstore](https://www.atlasrfidstore.com/rfid-insider/a-tag-a-label-an-inlay).

### Память чипа — по-человечески

В чипе стандарта Gen2 четыре «ящика» памяти. [atlasRFIDstore: Types of Memory in Gen 2](https://www.atlasrfidstore.com/rfid-insider/types-of-memory-in-gen-2-uhf-rfid-tags)

| Ящик | Что внутри | Аналогия для клиента |
|---|---|---|
| **EPC** | Главный номер, который вы записываете сами (обычно от 96 бит) | «Номер на бирке» — можно переписать |
| **TID** | Заводской номер чипа, ставит производитель, обычно не меняется | «Серийный номер с завода» — защита от подделки |
| **User** | Доп. память, есть не у всех чипов, обычно до ~512 бит | «Блокнот» — дата поверки, партия и т.п. |
| **Reserved** | Пароли (доступ, «убить» метку) | «Замок» — большинству не нужен |

Объём памяти конкретной метки смотрят в даташите (там же). Ещё один источник по банкам памяти: [TSC Printers: memory in RAIN RFID chips](https://emea.tscprinters.com/en/blog/your-guide-memory-rain-rfid-tag-chips).

---

## 3. Типы меток (для каталога)

| Тип | Что это | Куда клеить |
|---|---|---|
| **Этикетка (в рулоне)** | Бумага/плёнка с инлеем, печатается на принтере | Коробки, товар, документы, пластик, дерево |
| **Гибкая on-metal** | Тонкая этикетка с прослойкой для металла | Металлические ОС, инструмент, стеллажи |
| **Hard tag (корпусная)** | Инлей в пластике, крепится клеем/винтом/стяжкой | Тара, паллеты, улица, грязь, мойка |
| **С печатью и кодированием** | Этикетка, на которой уже напечатан текст/штрихкод и записан EPC | Клиенту остаётся только наклеить |

Определения этикетки и hard tag: [atlasRFIDstore](https://www.atlasrfidstore.com/rfid-insider/a-tag-a-label-an-inlay).
Пример, когда пришлось брать два типа (обычная + on-metal) при инвентаризации ОС: [кейс Cleverence / ПИМУ](https://www.cleverence.ru/projects/rfid/inventarizatsiya-imushchestva-bystree-v-8-raz/).

### Почему металл и вода мешают

- **Металл отражает** радиоволну и «сбивает настройку» антенны метки → обычная метка на железе не читается. [GS1: metal and water](https://support.gs1.org/support/solutions/articles/43000734154-does-rfid-work-around-metal-and-water-), [atlasRFIDstore: environment](https://www.atlasrfidstore.com/rfid-insider/factoring-environment-rfid-deployments/)
- **Вода и жидкости поглощают** волну → метке не хватает энергии ответить. (те же источники)

### Как это решает on-metal

У меток для металла есть **прослойка-«подушка»** и особая антенна: они держат расстояние от металла, и метка не «расстраивается». [RFID Journal: tags for metal](https://www.rfidjournal.com/news/how-do-rfid-tags-designed-for-metal-surfaces-function/176188/), [GS1](https://support.gs1.org/support/solutions/articles/43000734154-does-rfid-work-around-metal-and-water-)

**Пример для сайта:** «Обычная метка на металле — как радио в лифте: молчит. On-metal-метка приподнята на подушке и слышит ридер».

⚠ Механизм «металл становится частью антенны» в найденных источниках прямо не подтверждён — так не писать без отдельного источника.

---

## 4. От чего зависит дальность чтения

**Одну цифру не давать.** Даже GS1 пишет, что «типичной» метки нет. [GS1](https://support.gs1.org/support/solutions/articles/43000734166-what-is-the-read-range-for-a-typical-rfid-tag)

Факторы ([atlasRFIDstore: read range](https://www.atlasrfidstore.com/rfid-insider/improve-rfid-read-range/), если не указано иное):

1. **Размер метки** — больше антенна, дальше чтение.
2. **Поверхность** — металл и вода без спецметки резко снижают дальность.
3. **Как повёрнута метка** к антенне ридера.
4. **Антенна ридера** — усиление и поляризация (круговая читает метку под любым углом, линейная — дальше, но капризна к повороту).
5. **Мощность и чувствительность ридера.**
6. **Кабели и переходники** — длинный кабель «съедает» сигнал.
7. **Окружение** — металл вокруг, вода, другая радиотехника.
8. **Форма зоны чтения** важнее «максимальной дальности». [GS1](https://support.gs1.org/support/solutions/articles/43000734166-what-is-the-read-range-for-a-typical-rfid-tag)
9. **Разрешённая мощность в стране** — см. раздел 7.

**Для сайта:** «Скажите, на что клеите и чем читаете — подберём метку и пришлём образцы проверить у вас».

---

## 5. Оборудование (вспомогательное)

### Принтер-энкодер

Делает три вещи за один проход ([Cybra: verify RFID tags during printing](https://cybra.com/how-to-verify-rfid-tags-during-printing/)):
1. **Записывает** номер (EPC) в чип.
2. **Проверяет** — сразу читает, правильно ли записалось.
3. **Печатает** текст, штрихкод, QR.

Если метка бракованная — принтер печатает на ней **VOID** и делает следующую (там же).

**Аналогия:** «Принтер-энкодер — это принтер, который не только пишет на бумаге, но и "прошивает" метку внутри, и сам проверяет, что получилось».

### Ручной терминал (ТСД)

Это «смартфон со сканером»: читает RFID-метки и штрихкоды. Зачем:
- инвентаризация — пройти по складу/офису и посчитать всё;
- **поиск конкретной вещи** («горячо-холодно»);
- приёмка товара.

Источник по задачам: [Zebra MC3330xR spec](https://www.zebra.com/gb/en/products/spec-sheets/rfid/rfid-handhelds/mc3330xr.html) (заявлено: Android, сканер 1D/2D, до 900+ меток/с, номинал ~6 м — цифры производителя).

---

## 6. Где применяют + кейсы

| Сфера | Что метят | Источник |
|---|---|---|
| Склад | Товар, коробки, паллеты | [kkm-shop.kz: RFID склад](https://www.kkm-shop.kz/aut/rfid/warehouse/) |
| Основные средства | Мебель, техника, оборудование | [Cleverence: ОС](https://www.cleverence.ru/solutions/rfid-metki-dlya-inventarizatsii-osnovnykh-sredstv/) |
| Инструмент, спецодежда | Инструмент, СИЗ | [РСТ-Инвент: проекты](https://rst-invent.kz/realizovannye-proekty/) (Сургутнефтегаз — спецодежда) |
| Оборотная тара | Ящики, контейнеры, паллеты | [atlasRFIDstore: RTI](https://www.atlasrfidstore.com/rfid-applications/returnable-transport-items-rfid/); [РСТ-Инвент](https://rst-invent.kz/realizovannye-proekty/) (Питерформ — тара) |
| Производство | Детали, заказы на участках | [1cbit.kz: кейс кухни на заказ, Уральск](https://uralsk.1cbit.kz/company/press/publication/382232/) ⚠ страница не открылась, только заголовок из поиска |
| Розница | Товар в магазине, инвентаризация | [kkm-shop.kz: RFID в магазине](https://www.kkm-shop.kz/aut/rfid/retail/); [Impinj](https://www.impinj.com/library/blog/nfc-vs-rfid-and-rain-rfid-differences-and-similarities) |

### Реальные кейсы Казахстан / СНГ

- **Актобе, библиотека университета им. К. Жубанова** — более 30 000 книг переведены на RFID, внедрял «РСТ-Инвент» (август 2026). [Новости IT-канала](https://www.novostiitkanala.ru/news/detail.php?ID=197944) ⚠ библиотечные метки часто HF, не UHF — тип в статье не указан.
- **«Астана Балет»** — RFID-система инвентаризации (без цифр). [1cbit.kz](https://www.1cbit.kz/1csoft/rfid-proekty-dlya-kazakhstana/)
- **Казахстан, салон шуб** (город не указан) — быстрая инвентаризация на «1С:УТ для Казахстана». [1С:Решения](https://solutions.1c.ru/projects/1161890/) ⚠ страница не открылась, только заголовок.
- **Нижний Новгород, ПИМУ (Россия)** — инвентаризация ОС: обычные + on-metal метки, 3 ТСД Chainway C72, 2 принтера RFID. Главный корпус: 16 ч → 2 ч; заявлено ускорение в 8 раз. [Cleverence](https://www.cleverence.ru/projects/rfid/inventarizatsiya-imushchestva-bystree-v-8-raz/)
- **Россия, разные отрасли:** ФНС (телеком-оборудование), Ю-Ур. ж/д (МТР), Сургутнефтегаз (спецодежда), Питерформ (тара). [РСТ-Инвент](https://rst-invent.kz/realizovannye-proekty/)

---

## 7. Частоты в Казахстане

**Подтверждено:** полоса **865,0–868,0 МГц** для RFID есть в правилах к **Приказу №34** от 21.01.2015 (рег. в Минюсте №10730 от 15.04.2015).

- Реквизиты приказа №34 / рег. №10730: [zakon.uchet.kz V1500010730](https://zakon.uchet.kz/rus/docs/V1500010730)
- В **приложении 1** (РЭС, на которые правила не распространяются), в редакции изменений **2017 года** (приказ №270, рег. №15954), **строка 31 «SRD (применения радиочастотной идентификации)»**: **865,0–868,0 МГц, 100 мВт, ширина канала до 200 кГц**. Там же 2446–2454 МГц для RFID. [zakon.uchet.kz V1700015954](https://zakon.uchet.kz/rus/docs/V1700015954)

**⚠ Важно, проверить до публикации:**
1. В 2022 году правила **изложены в новой редакции** (приказ №64/НҚ от 24.02.2022, действует с 01.05.2022). Текст актуального приложения 1 я открыть не смог (платный доступ / JS). [prg.kz](https://prg.kz/Document/?doc_id=33319185) Также были изменения 18.10.2022 №388/НҚ (рег. №30273) — про RFID там ничего не нашёл. [zakon.uchet.kz V2200030273](https://zakon.uchet.kz/rus/docs/V2200030273)
2. **100 мВт — это мало.** Многие ридеры работают на большей мощности. Если лимит действует и сейчас, на сайте **не обещать** дальность «как в Европе/России» и проверить мощность своих ридеров (SIR7303, SLR5318) на соответствие. Единица (э.и.и.м./ERP) в пересказе не уточнена.
3. В сводке GS1 по UHF-регулированию (ноябрь 2024) **Казахстана нет** — сослаться на неё нельзя. [GS1 uhf_regulations.pdf](https://www.gs1.org/docs/epc/uhf_regulations.pdf)

**Как писать на сайте (безопасно):** «Наши метки работают в диапазоне 865–868 МГц, разрешённом в Казахстане» — со ссылкой на приказ №34. Без цифр мощности.

---

## 8. Частые вопросы клиентов (черновик FAQ)

1. **Чем RFID лучше штрихкода?** Не нужно наводить сканер на каждую вещь — ридер читает сотни меток сразу, даже в коробке. [Impinj](https://www.impinj.com/library/blog/rfid-vs-barcodes-pros-cons-and-how-they-work-together)
2. **На каком расстоянии читается?** Зависит от метки, поверхности и ридера — обычно несколько метров. Подберём под вашу задачу и дадим образцы проверить. [GS1](https://support.gs1.org/support/solutions/articles/43000734166-what-is-the-read-range-for-a-typical-rfid-tag)
3. **Работает ли на металле?** Обычная — нет. Для металла есть специальные on-metal метки. [GS1](https://support.gs1.org/support/solutions/articles/43000734154-does-rfid-work-around-metal-and-water-)
4. **А на бутылках с водой?** Вода мешает — подбираем метку и место крепления, обязательно тестируем на образцах. (там же)
5. **Нужна ли батарейка?** Нет, метка питается от сигнала ридера. [Impinj](https://www.impinj.com/library/blog/rfid-vs-barcodes-pros-cons-and-how-they-work-together)
6. **Можно ли напечатать на метке логотип и штрихкод?** Да, если это этикетка — печатаем и сразу записываем номер в чип. [Cybra](https://cybra.com/how-to-verify-rfid-tags-during-printing/)
7. **Что такое EPC?** Номер внутри метки, который связывает её с вашей карточкой товара/ОС в учёте. [atlasRFIDstore](https://www.atlasrfidstore.com/rfid-insider/types-of-memory-in-gen-2-uhf-rfid-tags)
8. **Можно ли подделать метку?** У каждого чипа есть заводской TID, его обычно нельзя изменить — по нему отличают оригинал. (там же) ⚠ формулировку «нельзя подделать» не использовать — защита зависит от системы.
9. **Можно ли перезаписать метку?** EPC — да, если его не заблокировали паролем. (там же)
10. **Нужен ли мой номер/формат EPC?** Можем закодировать по вашей схеме или предложить свою. *(внутренний ответ VenMart — уточнить)*
11. **Работает ли с 1С?** Да, обмен с 1С — часть нашего решения. *(внутренний ответ VenMart — уточнить; пример интеграции у других: [1cbit.kz](https://www.1cbit.kz/1csoft/rfid-proekty-dlya-kazakhstana/))*
12. **Что если метка не записалась?** Принтер проверяет каждую и помечает брак надписью VOID. [Cybra](https://cybra.com/how-to-verify-rfid-tags-during-printing/)
13. **Нужно ли разрешение на частоты?** Диапазон 865–868 МГц предусмотрен правилами РК (приказ №34). [zakon.uchet.kz](https://zakon.uchet.kz/rus/docs/V1700015954) ⚠ проверить текущую редакцию.
14. **Можно ли сначала попробовать?** Да — образцы. *(внутренний ответ VenMart — условия образцов уточнить)*
15. **Сколько стоит метка?** От цены за штуку до тысяч тенге — зависит от типа и тиража. *(внутренний ответ VenMart — нужны цены)*

---

## Источники (сводно)

- [Impinj: RFID vs Barcodes](https://www.impinj.com/library/blog/rfid-vs-barcodes-pros-cons-and-how-they-work-together)
- [Impinj: NFC vs RFID and RAIN RFID](https://www.impinj.com/library/blog/nfc-vs-rfid-and-rain-rfid-differences-and-similarities)
- [Impinj: UHF RFID vs RAIN RFID](https://www.impinj.com/library/blog/uhf-rfid-vs-rain-rfid-the-differences-and-similarities)
- [GS1: read range](https://support.gs1.org/support/solutions/articles/43000734166-what-is-the-read-range-for-a-typical-rfid-tag)
- [GS1: metal and water](https://support.gs1.org/support/solutions/articles/43000734154-does-rfid-work-around-metal-and-water-)
- [GS1: UHF regulations (PDF)](https://www.gs1.org/docs/epc/uhf_regulations.pdf)
- [atlasRFIDstore: tag, label, inlay](https://www.atlasrfidstore.com/rfid-insider/a-tag-a-label-an-inlay)
- [atlasRFIDstore: memory types](https://www.atlasrfidstore.com/rfid-insider/types-of-memory-in-gen-2-uhf-rfid-tags)
- [atlasRFIDstore: read range](https://www.atlasrfidstore.com/rfid-insider/improve-rfid-read-range/)
- [atlasRFIDstore: environment](https://www.atlasrfidstore.com/rfid-insider/factoring-environment-rfid-deployments/)
- [atlasRFIDstore: returnable transport items](https://www.atlasrfidstore.com/rfid-applications/returnable-transport-items-rfid/)
- [RFID Journal: tags for metal](https://www.rfidjournal.com/news/how-do-rfid-tags-designed-for-metal-surfaces-function/176188/)
- [Cybra: verify RFID tags during printing](https://cybra.com/how-to-verify-rfid-tags-during-printing/)
- [TSC: memory in RAIN RFID chips](https://emea.tscprinters.com/en/blog/your-guide-memory-rain-rfid-tag-chips)
- [Zebra MC3330xR spec sheet](https://www.zebra.com/gb/en/products/spec-sheets/rfid/rfid-handhelds/mc3330xr.html)
- [zakon.uchet.kz: приказ №34](https://zakon.uchet.kz/rus/docs/V1500010730), [изменения 2017](https://zakon.uchet.kz/rus/docs/V1700015954), [изменения 2022](https://zakon.uchet.kz/rus/docs/V2200030273), [prg.kz: новая редакция 2022](https://prg.kz/Document/?doc_id=33319185)
- [Cleverence: кейс ПИМУ](https://www.cleverence.ru/projects/rfid/inventarizatsiya-imushchestva-bystree-v-8-raz/), [Cleverence: ОС](https://www.cleverence.ru/solutions/rfid-metki-dlya-inventarizatsii-osnovnykh-sredstv/)
- [РСТ-Инвент: проекты](https://rst-invent.kz/realizovannye-proekty/), [Новости IT-канала: Актобе](https://www.novostiitkanala.ru/news/detail.php?ID=197944)
- [1cbit.kz: RFID в Казахстане](https://www.1cbit.kz/1csoft/rfid-proekty-dlya-kazakhstana/), [kkm-shop.kz: склад](https://www.kkm-shop.kz/aut/rfid/warehouse/), [kkm-shop.kz: магазин](https://www.kkm-shop.kz/aut/rfid/retail/)
