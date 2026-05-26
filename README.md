# AtomFlow

**Flask + SQLAlchemy + PostgreSQL**  
Веб-система для управления проектами, задачами, командной работой и мониторинга эффективности сотрудников (KPI).  
Включает чат, календарь, доску задач, диаграмму Ганта, рулетку с жетонами и ролевую модель (администратор/пользователь).

---

## Статистика проекта

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Flask](https://img.shields.io/badge/Flask-2.3-black)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-2.0-red)
![License](https://img.shields.io/badge/License-MIT-yellow)

![Code Size](https://img.shields.io/github/languages/code-size/aleksandrvolostnov/Information-system-for-managing-project-tasks-and-monitoring-efficiency)
![Lines of Code](https://img.shields.io/tokei/lines/github/aleksandrvolostnov/Information-system-for-managing-project-tasks-and-monitoring-efficiency)

---

## Технологический стек

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-CC0000?style=for-the-badge&logo=sqlalchemy&logoColor=white)
![Flask-Login](https://img.shields.io/badge/Flask--Login-000000?style=for-the-badge&logo=flask&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=for-the-badge&logo=chartdotjs&logoColor=white)
![OpenPyXL](https://img.shields.io/badge/OpenPyXL-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)

---

## Возможности системы

### 👥 Управление пользователями и ролями
- Роли: **администратор** и **обычный пользователь**
- Регистрация, авторизация, управление профилем (аватар, email, телефон)
- Администратор: создание/удаление пользователей, смена ролей и паролей

### 📁 Проекты
- Создание проектов с названием и описанием
- Добавление/удаление участников проекта
- Просмотр задач проекта в разрезе готовности, приоритета, сложности

### ✅ Задачи
- Создание, редактирование, удаление задач
- Атрибуты: название, описание, приоритет, статус, сложность, дедлайн, исполнитель
- Привязка задач к проектам
- Вложенные файлы (изображения, документы)
- Комментарии к задачам (с редактированием и удалением)
- Подзадачи (для диаграммы Ганта)
- Автоматическая отметка просроченных задач

### 📊 Доска задач
- Три представления: по **статусу** (В работе / Выполненные / Просроченные), по **приоритету**, по **сложности**
- Drag-and-drop (перетаскивание между колонками с сохранением в БД)

### 📅 Календарь
- Отображение задач на выбранный месяц
- Подсчёт задач по приоритету и сложности

### 📈 KPI и отчёты
- Расчёт индивидуального KPI сотрудника на основе выполненных задач (с учётом веса: сложность × приоритет)
- Общий KPI компании
- Экспорт отчёта в Excel (за выбранный период) – для одного сотрудника или всех (только админ)
- Диаграмма (bar chart) в Excel

### 💬 Чат (личные и групповые сообщения)
- Личные сообщения между пользователями
- Общая групповая беседа
- Отправка файлов
- Ответы на сообщения (threads)
- Пересылка сообщений
- Отметка о прочитанном

### 🔔 Напоминания
- Создание напоминаний с датой/временем, приоритетом, повторением (нет/ежедневно/еженедельно/ежемесячно)
- Отдельная страница со списком напоминаний

### 📐 Диаграмма Ганта
- Визуализация задач и подзадач на временной шкале
- Добавление/редактирование/удаление подзадач через интерфейс

### 📎 Редактирование документов (OnlyOffice)
- Загрузка файлов (docx, xlsx, pptx, txt)
- Интеграция с OnlyOffice Document Server для онлайн-редактирования

---

## Быстрый старт

### Предварительные требования
- Python 3.10+
- PostgreSQL (создайте базу данных, например `efficiency_control`)
- (опционально) OnlyOffice Document Server для редактирования документов

### Локальный запуск

```bash
# Клонирование репозитория
git clone https://github.com/aleksandrvolostnov/Information-system-for-managing-project-tasks-and-monitoring-efficiency.git
cd Information-system-for-managing-project-tasks-and-monitoring-efficiency

# Установка зависимостей
pip install -r requirements.txt

# Создание таблиц и заполнение начальными данными
# Откройте psql или любой клиент PostgreSQL и выполните SQL из файла init_db.sql (приведён ниже)
Создание таблиц и начальных данных (SQL)
Выполните следующие скрипты в вашей базе данных:
-- 1. Таблица ролей
CREATE TABLE roles (
    id SERIAL PRIMARY KEY,
    role_name VARCHAR(50) NOT NULL
);

-- 2. Таблица пользователей
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(150) NOT NULL UNIQUE,
    password VARCHAR(150) NOT NULL,
    role_id INTEGER REFERENCES roles(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    email VARCHAR(150) UNIQUE,
    phone VARCHAR(20),
    avatar VARCHAR(255),
    tokens INTEGER DEFAULT 0
);

-- 3. Проекты
CREATE TABLE projects (
    id SERIAL PRIMARY KEY,
    name VARCHAR(150) NOT NULL,
    description TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    owner_id INTEGER NOT NULL REFERENCES users(id)
);

-- 4. Связь проектов и пользователей
CREATE TABLE project_members (
    project_id INTEGER NOT NULL REFERENCES projects(id) ON DELETE CASCADE,
    user_id INTEGER NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    PRIMARY KEY (project_id, user_id)
);

-- 5. Напоминания
CREATE TABLE reminders (
    id SERIAL PRIMARY KEY,
    title VARCHAR(150) NOT NULL,
    description TEXT,
    reminder_date TIMESTAMP NOT NULL,
    priority VARCHAR(50) DEFAULT 'Низкий',
    repeat VARCHAR(50) DEFAULT 'Нет',
    user_id INTEGER NOT NULL REFERENCES users(id)
);

-- 6. Задачи
CREATE TABLE tasks (
    id SERIAL PRIMARY KEY,
    title VARCHAR(150) NOT NULL,
    description TEXT NOT NULL,
    priority VARCHAR(50) NOT NULL,
    status VARCHAR(50) NOT NULL,
    difficulty VARCHAR(50) NOT NULL,
    due_date TIMESTAMP NOT NULL,
    user_id INTEGER REFERENCES users(id),
    assigned_to_id INTEGER REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    project_id INTEGER NOT NULL REFERENCES projects(id),
    parent_task_id INTEGER REFERENCES tasks(id)
);

-- 7. Подзадачи
CREATE TABLE subtasks (
    id SERIAL PRIMARY KEY,
    task_id INTEGER NOT NULL REFERENCES tasks(id),
    title VARCHAR(150) NOT NULL,
    start_date TIMESTAMP NOT NULL,
    end_date TIMESTAMP NOT NULL
);

-- 8. Комментарии к задачам
CREATE TABLE task_comments (
    id SERIAL PRIMARY KEY,
    task_id INTEGER NOT NULL REFERENCES tasks(id),
    user_id INTEGER NOT NULL REFERENCES users(id),
    comment TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 9. Файлы
CREATE TABLE files (
    id SERIAL PRIMARY KEY,
    filename VARCHAR(255) NOT NULL,
    task_id INTEGER REFERENCES tasks(id)
);

-- 10. Сообщения
CREATE TABLE messages (
    id SERIAL PRIMARY KEY,
    sender_id INTEGER NOT NULL REFERENCES users(id),
    receiver_id INTEGER REFERENCES users(id),
    is_group BOOLEAN DEFAULT FALSE,
    content TEXT,
    filename VARCHAR(150),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    is_read BOOLEAN DEFAULT FALSE,
    parent_message_id INTEGER REFERENCES messages(id)
);

-- Начальные данные
INSERT INTO roles (role_name) VALUES ('admin'), ('user');


# Настройка подключения к БД в app.py
# В строке: app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://postgres:1111@localhost/efficiency_control'
# Укажите свои логин/пароль/хост/имя БД

# Запуск приложения
python app.py
Откройте браузер: http://127.0.0.1:5000


