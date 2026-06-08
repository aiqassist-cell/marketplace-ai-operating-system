# Airtable MVP: Виртуальный Офис QWEAR

Дата решения: 2026-06-08

## Цель

Собрать дружелюбный интерфейс виртуального офиса, в котором видно:

- какие товары находятся в фокусе;
- какие задачи выполняют агенты;
- что требует согласования человека;
- какие гипотезы тестируются;
- какой контент готовится и публикуется;
- какие результаты стали winners.

## Структура Базы

### 1. Products

Главная сущность системы. Одна запись равна одной модели / артикулу.

Обязательные поля:

| Поле | Тип Airtable | Назначение |
|---|---|---|
| Product ID | Single line text | Стабильный ID |
| Name | Single line text | Название модели |
| Marketplace SKU | Single line text | Артикул WB/Ozon |
| Marketplace URL | URL | Ссылка на карточку |
| Product Family | Single select | Семейство модели |
| Status | Single select | Candidate / Focus / Active / Paused / Closed |
| Priority | Single select | High / Medium / Low |
| Price | Currency | Текущая цена |
| Sizes | Multiple select | Размерный ряд |
| Material | Long text | Состав и фактура |
| Seasonality | Single select | All season / Long / Medium / Short / Event |
| Plus Size Potential | Single select | Confirmed / Needs validation / No |
| Stock | Number | Остаток |
| Buyout Rate | Percent | Фактический выкуп |
| Product Score | Number | Скоринг продуктолога |
| Main Promise | Long text | Главное обещание |
| Main Risk | Long text | Главный риск |
| Drive Folder | URL | Папка материалов |
| Owner Approval | Checkbox | Согласование владельца |

Связи:

- Tasks;
- Hypotheses;
- Content Assets;
- Publications;
- Results;
- Approvals.

### 2. Agents

Реестр виртуальных сотрудников и их текущей загрузки.

| Поле | Тип Airtable |
|---|---|
| Agent ID | Single line text |
| Agent Name | Single line text |
| Role | Single select |
| Contour | Single select: First / Support / Production |
| Status | Single select: Active / Paused |
| Instructions URL | URL |
| Current Tasks | Link to Tasks |
| Open Task Count | Count |
| Last Run | Date/time |
| Last Error | Long text |

### 3. Tasks

Центральная очередь работы виртуального офиса.

| Поле | Тип Airtable |
|---|---|
| Task ID | Single line text |
| Task Name | Single line text |
| Product | Link to Products |
| Assigned Agent | Link to Agents |
| Status | Single select: Backlog / Ready / In progress / Blocked / Review / Done / Cancelled |
| Priority | Single select |
| Input | Long text |
| Expected Output | Long text |
| Result | Long text |
| Result URL | URL |
| Due Date | Date |
| Needs Approval | Checkbox |
| Blocker | Long text |
| n8n Run ID | Single line text |
| Created At | Created time |
| Updated At | Last modified time |

### 4. Hypotheses

Хранит продуктовые, маркетинговые, SMM и карточные гипотезы.

| Поле | Тип Airtable |
|---|---|
| Hypothesis ID | Single line text |
| Product | Link to Products |
| Type | Single select: Product / Demand / Content / Photo / Price |
| Statement | Long text |
| Fact | Long text |
| Risk | Long text |
| What To Check | Long text |
| Metric | Multiple select |
| Status | Single select: Draft / Approved / Testing / Winner / Rejected |
| Decision | Long text |
| Owner Approval | Checkbox |

### 5. Content Assets

Все единицы rich-контента, инфографики, фото и видео.

| Поле | Тип Airtable |
|---|---|
| Asset ID | Single line text |
| Product | Link to Products |
| Asset Name | Single line text |
| Asset Type | Single select: Rich / Infographic / Photo / Video / Hook / Production brief |
| Funnel Stage | Single select: Attention / Benefit / Proof / Objection / Purchase |
| Platform | Multiple select |
| Hook | Long text |
| CTA | Long text |
| Status | Single select: Idea / Brief / Production / Review / Approved / Rejected |
| File | Attachment |
| Drive URL | URL |
| Approved For Card | Checkbox |
| Approved For Social | Checkbox |
| QA Notes | Long text |

### 6. Publications

План и факт публикаций в социальных сетях.

| Поле | Тип Airtable |
|---|---|
| Publication ID | Single line text |
| Product | Link to Products |
| Asset | Link to Content Assets |
| Platform | Single select: TikTok / Reels / Shorts / VK Clips / Telegram / Pinterest |
| Account | Single line text |
| Planned Date | Date/time |
| Published Date | Date/time |
| Status | Single select: Planned / Ready / Published / Stop |
| URL | URL |
| Views | Number |
| Completion Rate | Percent |
| Saves | Number |
| Comments | Number |
| Clicks | Number |
| Orders | Number |
| Winner Status | Single select: Test / Winner / Scale / Stop |
| Insight | Long text |

### 7. Results

Сводные измеримые результаты по товару и периоду.

| Поле | Тип Airtable |
|---|---|
| Result ID | Single line text |
| Product | Link to Products |
| Period Start | Date |
| Period End | Date |
| Views | Number |
| Clicks | Number |
| Favorites | Number |
| Carts | Number |
| Orders | Number |
| Buyout Rate | Percent |
| Revenue | Currency |
| Margin | Currency |
| Conclusion | Long text |
| Next Action | Long text |

### 8. Approvals

Очередь решений, которые нельзя принимать автономно.

| Поле | Тип Airtable |
|---|---|
| Approval ID | Single line text |
| Product | Link to Products |
| Related Task | Link to Tasks |
| Approval Type | Single select: Product launch / Content / Card change / Budget / Price / Production |
| Question | Long text |
| Recommendation | Long text |
| Risk | Long text |
| Status | Single select: Pending / Approved / Rejected / Needs revision |
| Decision Comment | Long text |
| Decision Date | Date/time |

## Интерфейсы Airtable

### Кабинет Владельца

Показывает только решения и ключевые сигналы:

- товары в фокусе;
- ожидающие согласования;
- заблокированные задачи;
- winners;
- продажи и результаты;
- кнопки `Согласовать`, `Отклонить`, `Вернуть на доработку`.

### Рабочая Зона Агентов

Показывает:

- очередь задач по статусам;
- задачи каждого агента;
- входные данные;
- результат;
- ошибки n8n;
- задачи, которым не хватает данных.

### Контент-Центр

Показывает:

- галерею rich-контента;
- календарь публикаций;
- production pipeline;
- assets на согласовании;
- winners по площадкам;
- контент по каждому товару.

## Основные Views

### Products

- `Focus Products`;
- `Needs Product Review`;
- `Low Stock`;
- `Plus Size Validation`;
- `Paused`.

### Tasks

- `Ready for n8n`;
- `In Progress`;
- `Blocked`;
- `Needs Human Review`;
- `Done This Week`;
- Kanban по статусу.

### Content Assets

- Gallery `Needs Approval`;
- Gallery `Approved Rich`;
- `Production Queue`;
- `Rejected / Fix Required`.

### Publications

- Calendar;
- `Ready to Publish`;
- `Winners`;
- `Stop / Replace`.

## Автоматизации Airtable

На старте Airtable отвечает только за простые действия:

1. При создании Product со статусом `Focus` создать Approval на запуск анализа.
2. При смене Task на `Review` уведомить владельца.
3. При Approval `Approved` отправить webhook в n8n.
4. При Publication `Winner` создать задачу SMM `Создать версии winner`.
5. При низком Stock создать предупреждение Manager и Logistics.

Сложные цепочки агентов остаются в n8n.

## n8n Webhooks

Рекомендуемые точки входа:

```text
POST /product-focus
POST /approval-approved
POST /task-ready
POST /content-approved
POST /publication-winner
```

## MVP Граница

Для первого запуска создаем только:

- Products;
- Agents;
- Tasks;
- Content Assets;
- Approvals.

После первого успешного прогона добавляем:

- Hypotheses;
- Publications;
- Results.

## Порядок Создания

1. Создать пустую Airtable Base `QWEAR Virtual Office`.
2. Импортировать CSV из `airtable-import/`.
3. Преобразовать указанные поля в Link to another record.
4. Настроить select options и типы полей.
5. Создать три интерфейса.
6. Подключить n8n только после ручного теста процесса.

