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


#### Шаг 4: Инициализируем Git и отправляем на GitHub (через SSH!)
Выполни эти команды по очереди. **Обрати внимание:** мы используем `git@github.com`, чтобы Git не спрашивал пароль.


# 1. Удаляем старый git, чтобы начать чисто (не бойся, коммиты ролей уже на GitHub)
rm -rf .git

# 2. Инициализируем новый репозиторий
git init

# 3. Переименовываем ветку в main
git branch -M main

# 4. Добавляем удаленный репозиторий через SSH (ВАЖНО!)
git remote add origin git@github.com:Warret/ansible-04-role-playbook.git

# 5. Добавляем все файлы
git add .

# 6. Делаем коммит
git commit -m "feat: ansible-04-role playbook with external dependencies"

# 7. Ставим тег версии
git tag 1.0.0

# 8. Отправляем на GitHub (если спросит про fingerprint, пиши yes)
git push -u origin main --tags
