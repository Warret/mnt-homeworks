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

<img width="930" height="449" alt="изображение" src="https://github.com/user-attachments/assets/b2271a54-4d88-40d8-83d4-dd8c7b2f8566" />

<img width="963" height="511" alt="изображение" src="https://github.com/user-attachments/assets/81cf0b57-4d21-4ae7-982e-5316b400630b" />
