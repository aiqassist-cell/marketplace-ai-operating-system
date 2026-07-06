# Project Handoff: QWEAR Virtual Office / Seller AI Team

Дата архива: 2026-07-06

## Назначение

Проект описывает систему цифровых сотрудников для бренда женской повседневной одежды QWEAR.

Цель: собрать виртуальный офис, который помогает управлять ассортиментом, маркетингом, SMM, rich-контентом, production, фотоворонкой карточки и первыми контентными тестами.

## Текущий Статус

Создан локальный git-репозиторий:

```text
seller-ai-team
```

Состояние: рабочее дерево чистое, последний коммит:

```text
ab1c47b Design Airtable virtual office MVP
```

GitHub remote был настроен ранее, но push не выполнен из-за отсутствия авторизации на машине.

## Главные Решения

### 1. SMM - агент первого контура

SMM / Distribution / World Manager поднят в первый контур наряду с маркетологом, потому что закрывает отсутствующую штатную единицу.

Он отвечает за:

- TikTok / Reels / Shorts / VK / Telegram / Pinterest;
- тренды;
- хуки;
- первый кадр;
- контент-план;
- публикации;
- weekly report;
- winners;
- обратную связь аудитории.

### 2. Digital Stylist - не просто стилист, а Content Funnel Designer

Digital Stylist превращен в агента контентных воронок:

- rich-контент;
- инфографика;
- сценарии носки;
- образы;
- брифы на оживление картинок;
- контентные касания от внимания до покупки.

### 3. Виртуальный офис строится на Airtable

Google Sheets заменен как основной интерфейс на Airtable.

Решение:

```text
Airtable = интерфейс и операционные данные
Google Drive / существующие Sheets = файлы и производственные данные
n8n = процессы и расписания
OpenAI = агенты и решения
MCP / API = внешние данные и инструменты
человек = контроль критических решений
```

### 4. MVP не строится как отдельное приложение

Отдельный web-интерфейс откладывается.

Сначала:

- Airtable Base;
- импорт CSV;
- ручной тест процесса;
- затем n8n;
- затем Apify / Firecrawl / WB-Ozon API.

## Структура Проекта

```text
agents/              Описания цифровых сотрудников
airtable-import/     CSV для импорта Airtable MVP
brand/               Позиционирование QWEAR
content-factory/     Принципы контент-завода и дистрибуции
docs/                Архитектура, решения, адаптации
pilots/              Первый пилот по коричневому платью
products/            Шаблоны готовых решений
templates/           Рабочие шаблоны агентов
```

## Созданные Агенты

### Первый контур

- `agents/productologist.md` - QWEAR Productologist Agent.
- `agents/marketer-strategist.md` - Marketer Strategist Agent.
- `agents/smm-world-manager.md` - SMM / Distribution / World Manager Agent.

### Поддерживающий контур

- `agents/digital-stylist.md` - Digital Stylist / Content Funnel Designer.
- `agents/manager-project-lead.md` - Manager / Project Lead.
- `agents/data-collector.md` - Data Collector.

### Production / карточка

- `agents/ai-production-lead.md` - AI Production Lead.
- `agents/photo-funnel.md` - Photo Funnel / Marketplace Card Visual Agent.

### Еще не доработаны

- `agents/finance-analyst.md` - пока базовый.
- `agents/logistics.md` - пока базовый.

## Ключевые Документы

- `README.md` - обзор проекта.
- `docs/system-architecture.md` - роли и связи агентов.
- `docs/agent-creation-order.md` - текущая очередность и приоритеты.
- `docs/virtual-office-technical-architecture.md` - техническая архитектура.
- `docs/airtable-mvp-design.md` - структура Airtable Base.
- `brand/positioning.md` - позиционирование QWEAR.
- `docs/rich-content-reference-qwear.md` - паттерны текущего rich-контента.
- `docs/syntez25-content-factory-adaptation.md` - адаптация презентации по контент-заводу.
- `pilots/2026-06-brown-basic-dress/pilot-brief.md` - первый пилот.

## Airtable MVP

Подготовлены CSV:

```text
airtable-import/Products.csv
airtable-import/Agents.csv
airtable-import/Tasks.csv
airtable-import/Content Assets.csv
airtable-import/Approvals.csv
airtable-import/Hypotheses.csv
airtable-import/Publications.csv
airtable-import/Results.csv
```

Назначение:

- быстро создать Base `QWEAR Virtual Office`;
- проверить интерфейс;
- прогнать первый товар;
- затем подключать n8n.

## Первый Пилот

Пилот:

```text
pilots/2026-06-brown-basic-dress/pilot-brief.md
```

Рабочий товар:

```text
Коричневое базовое платье / платье-футболка / миди-макси
```

Гипотеза:

```text
Если показывать платье не как отдельный товар, а как базу для нескольких сценариев жизни,
то должны расти сохранения, переходы, избранное, корзина и качество вопросов.
```

Пока не хватает:

- артикул WB/Ozon;
- ссылка на карточку;
- цена;
- размерный ряд;
- состав;
- отзывы;
- вопросы;
- остатки;
- текущие метрики.

## Source Materials

В архив дополнительно включается папка:

```text
source-materials/
```

Она содержит исходные материалы, которые использовались как референсы:

- handoff по продуктологу;
- PDF СИНТЕЗ25 по контент-заводу;
- скриншоты rich-контента;
- скриншоты структуры контент-завода.

Если какой-то файл отсутствует в Downloads на момент сборки, это не блокирует проект: все ключевые выводы уже перенесены в `docs/`.

## История Коммитов

```text
ab1c47b Design Airtable virtual office MVP
bcf6756 Document virtual office technical architecture
fd3250d Create brown basic dress pilot
e98dd04 Define photo funnel marketplace card agent
f3410bb Define AI production lead agent
84492ba Update QWEAR brand positioning
ac7f8f4 Promote SMM to first contour agent
f5c999a Define SMM distribution world manager agent
8db9edc Define marketer strategist agent
aead1ed Add QWEAR rich content reference patterns
6d8011d Add TikTok to content funnel templates
6ec4a45 Expand digital stylist into content funnel designer
3f1b930 Add Syntez25 content factory adaptation
631330a Define digital stylist agent
b9bc866 Define manager project lead agent
90294ce Define QWEAR productologist agent
2d119fd Initial marketplace AI operating system
```

## Следующие Шаги

1. Создать Airtable Base `QWEAR Virtual Office`.
2. Импортировать CSV из `airtable-import/`.
3. Настроить связи между таблицами.
4. Создать интерфейсы:
   - кабинет владельца;
   - рабочая зона агентов;
   - контент-центр.
5. Внести реальный артикул и данные коричневого платья.
6. Прогнать первый workflow вручную.
7. После ручной проверки подключать n8n.
8. После n8n подключать Apify / Firecrawl / WB-Ozon API.

## Важные Ограничения

- AI-изображения нельзя переносить в карточку без проверки соответствия реальному товару.
- Нельзя обещать plus size без подтвержденной посадки и лекал.
- SMM не заменяет маркетолога; он отвечает за социальную механику и дистрибуцию.
- Marketer не заменяет Productologist; он отвечает за спрос, оффер и коммерческую гипотезу.
- На старте критические решения должны согласовываться человеком.

