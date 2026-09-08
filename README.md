# Ansible Playbook: ClickHouse + Vector + Lighthouse (Roles)

## Описание
Данный репозиторий содержит playbook для развертывания стека мониторинга с использованием Ansible Roles. 
Роли для Vector и Lighthouse разработаны самостоятельно и вынесены в отдельные репозитории. Роль для ClickHouse подключается как внешняя зависимость.

## Структура
- `site.yml` — основной playbook, вызывающий роли.
- `Inventory/prod.yml` — инвентарь с хостами и переменными подключения.
- `requirements.yml` — зависимости (роли), которые скачиваются перед запуском.

## Как использовать
1. Установите зависимости (роли будут скачаны в папку `roles/`):
   ```bash
   ansible-galaxy install -r requirements.yml -p roles

Ссылки на репозитории ролей:
    vector-role - https://github.com/Warret/ansible-vector-role
    lighthouse-role - https://github.com/Warret/ansible-lighthouse-role

2. Запустите playbook:
    ansible-playbook -i Inventory/prod.yml site.yml --diff


