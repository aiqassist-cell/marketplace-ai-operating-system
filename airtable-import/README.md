# Airtable Import

Стартовые CSV для базы `QWEAR Virtual Office`.

## Импорт

1. Создайте новую Airtable Base.
2. Импортируйте каждый CSV как отдельную таблицу.
3. Переименуйте таблицы без суффикса `.csv`.
4. Настройте типы полей по документу:
   `docs/airtable-mvp-design.md`.
5. Преобразуйте текстовые ссылки в `Link to another record`:
   - `Tasks.Product ID` -> `Products`;
   - `Tasks.Agent ID` -> `Agents`;
   - `Content Assets.Product ID` -> `Products`;
   - `Approvals.Product ID` -> `Products`;
   - `Approvals.Task ID` -> `Tasks`.

CSV специально оставлены простыми: сначала импорт и ручная проверка, затем n8n.

