# Ansible Playbook: ClickHouse + Vector + Lighthouse

## Описание
Данный playbook автоматизирует развертывание стека для сбора и визуализации логов в Yandex Cloud. Он полностью идемпотентен и проходит проверку `ansible-lint` без ошибок.

## Структура проекта
- `Inventory/prod.yml` — инвентарь с группами хостов (`clickhouse`, `vector`, `lighthouse`) и переменными подключения.
- `site.yml` — основной playbook, состоящий из 3 play (по одному на каждый сервис).
- `templates/` — Jinja2 шаблоны конфигурационных файлов (`nginx.conf.j2`, `vector.yaml.j2`).

## Как использовать
1. Убедитесь, что у вас есть доступ по SSH к хостам (ключ указан в `Inventory/prod.yml`).
2. Проверьте синтаксис: `ansible-lint site.yml`
3. Запустите в тестовом режиме: `ansible-playbook -i Inventory/prod.yml site.yml --check --diff`
4. Запустите развертывание: `ansible-playbook -i Inventory/prod.yml site.yml --diff`

## Параметры и Теги
- **Параметры**: Все необходимые переменные (пользователь, путь к ключу, IP-адреса) вынесены в `Inventory/prod.yml`.
- **Теги**: В данной версии теги не используются, так как playbook спроектирован для целостного развертывания всех трех сервисов за один проход. При необходимости теги можно добавить к отдельным задачам (например, `tags: lighthouse`).