AtomFlow — Система управления проектами, задачами и эффективностью
Flask + PostgreSQL + DHTMLX Gantt
Веб-приложение для тотального контроля над проектами, задачами, корпоративным чатом и аналитикой эффективности.
Подходит для малых и средних команд, которые хотят видеть полную картину: кто, что, когда делает и не терять коммуникацию.

Статистика проекта
https://img.shields.io/badge/Python-3.9%252B-blue
https://img.shields.io/badge/Flask-2.0-black
https://img.shields.io/badge/PostgreSQL-16-4169E1
https://img.shields.io/badge/DHTMLX%2520Gantt-9.0-FF7F50
https://img.shields.io/badge/Choices.js-11.0-FFB13B

https://img.shields.io/github/languages/code-size/aleksandrvolostnov/Information-system-for-managing-project-tasks-and-monitoring-efficiency
https://img.shields.io/badge/DB-PostgreSQL-blue
https://img.shields.io/badge/License-MIT-yellow

Технологический стек
https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white
https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white
https://img.shields.io/badge/SQLAlchemy-CC0000?style=for-the-badge&logo=sqlalchemy&logoColor=white
https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black
https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white
https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white
https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white

📂 Основной проект
Проект	Описание	Стек	Ссылка
AtomFlow	Система управления проектами и задачами с чатом, календарём, диаграммой Ганта и аналитикой эффективности	https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white https://img.shields.io/badge/Flask-000000?logo=flask&logoColor=white https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white https://img.shields.io/badge/JS-F7DF1E?logo=javascript&logoColor=black	GitHub
Возможности системы
👥 Пользователи и роли
Регистрация / авторизация (Flask‑Login)

Разделение ролей: Администратор (полный доступ) и Пользователь

📁 Проекты
Создание проектов, приглашение участников

Просмотр деталей и динамики проекта

✅ Задачи
Приоритет: Низкий / Средний / Высокий

Статус: Выполняется, Завершена, Просрочена и др.

Сложность (1–3 балла)

Дедлайн с визуальной подсветкой просрочек

Подзадачи и зависимости между задачами

Загрузка множества файлов к каждой задаче

Назначение ответственного исполнителя

📅 Календарь
Месячный просмотр всех задач

Группировка по датам

Аналитика по приоритетам и сложности на выбранный период

💬 Корпоративный мессенджер
Личные и групповые чаты

Отправка текста и файлов

Уведомления о непрочитанных сообщениях

Ответы на сообщения и пересылка

📊 Дашборд и аналитика
Виджет «3 ближайшие задачи» (самые горящие дедлайны)

Общая статистика по приоритетам и сложности задач

Графики распределения нагрузки

⏰ Напоминания
Персональные напоминания с настройкой повторения

Приоритет напоминаний

📈 Диаграмма Ганта
Визуализация проектов с помощью dhtmlx-gantt

Drag‑and‑drop изменение сроков

✏️ Интеграция с OnlyOffice
Встроенный редактор документов (в коде обозначен как KM SOFT)

Быстрый старт
Локальный запуск
bash
# 1. Клонировать репозиторий
git clone https://github.com/aleksandrvolostnov/Information-system-for-managing-project-tasks-and-monitoring-efficiency.git
cd Information-system-for-managing-project-tasks-and-monitoring-efficiency

# 2. Создать и активировать виртуальное окружение
python -m venv venv
source venv/bin/activate      # Linux/Mac
venv\Scripts\activate         # Windows

# 3. Установить Python-зависимости
pip install flask flask_sqlalchemy flask_login babel werkzeug openpyxl psycopg2-binary

# 4. Установить frontend-зависимости (Choices.js, DHTMLX Gantt)
npm install

# 5. Настроить PostgreSQL
#    Создайте базу данных, например 'efficiency_control'
#    В файле app.py измените строку подключения:
#    app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://пользователь:пароль@localhost/имя_бд'

# 6. Создать таблицы в БД
python
>>> from app import db
>>> db.create_all()
>>> exit()

# 7. Запустить приложение
python app.py
Открой в браузере: http://127.0.0.1:5000
