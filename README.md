# AllRussia Backend
## Содержание
- [Технологии](#технологии)
- [Установка и настройка](#установка-и-настройка)
- [Маршруты и функциональность](#маршруты-и-функциональность)
    - [Маршруты](#маршруты)
    - [Структура новостей](#структура-новостей)
    - [Новости для главной страницы](#новости-для-главной-страницы)
- [Файловая структура](#файловая-структура)

## Технологии
- Python
- Flask
- pandas
- PostgreSQL
- SQLAlchemy
- alembic


*Полный список зависимостей хранится в файле `backend/requirements.txt`.*

## Установка и настройка
1. Сделайте форк репозитория
2. Склонируйте созданный форк:
```bash
git clone git@github.com:<ваш-никнейм>/AllRussia-backend.git
cd AllRussia-backend
```
3. Cоздайте и активируйте виртуальное окружение:
```bash
cd backend
python -m venv venv

# Для Windows
. venv/scripts/activate
# Для Linux
source venv/bin/activate 
```
4. Установите зависимости:
```bash
pip install -r requirements.txt
```
5. Запустите проект:
```bash
python app.py
```
6. TODO - запуск и конфигурация БД и миграций

## Маршруты и функциональность
### Маршруты:
| Название маршрута | Маршрут |
|------------|------------|
| Вход в админ-панель: |http://localhost:5000/adm_login |
| Новости "Политика" | http://localhost:5000/data_news_politics |
| Новости "Экономика" | http://localhost:5000/data_news_economics |
| Новости "Наука и образование" | http://localhost:5000/data_news_science_education |
| Новости "Культура и история" | http://localhost:5000/data_culture_history |
| Новости "Спорт" | http://localhost:5000/data_news_sport |
| Новости "Туризм" | http://localhost:5000/data_news_tourism |
| Новости "Партнеры" | http://localhost:5000/data_news_partners |
| Новости "Проекты" | http://localhost:5000/data_news_projects |
| Новости для главной страницы | http://localhost:5000/data_main_page |

Все новости отсортированы по **убыванию даты добавления**.

### Структура новостей
```json
{
    "id": 12,
    "url": "flags.jpg",
    "title": "Новый курорт предложил уникальные условия для отдыха на море",
    "subtitle": "12313213123131",
    "tag": "Туризм",
    "updated": "2024-04-11 15:32:34"
}
```
`id` - идентификатор в БД, `url` - название и расширение файла картинки новости в папке проекта, `title` - заголовок, `subtitle` - содержание статьи, `tag` - тема статьи, `updated` - дата и время последнего изменения.

### Новости для главной страницы
1. Одна главная новость **main_article**
2. 6 новостей, похожих на главную **same_as_main**
3. 6 самых последних новостей **last_news**
4. 2 последние по политике **politics**
5. 4 последние по экономике **economics**
6. 5 последних по науке **science_education**
7. 4 последних по культуре и истории **culture_history**
8. 4 последних по спорту **sport**
9. 4 последних по туризму **tourism**
10. 4 последних по партнерам **partners**
11. 4 последних по проектам **projects**


## Файловая структура
```bash
ALLRUSSIA/
├── backend/
│   ├── public/
│   ├── scripts/ 
│   │   ├── cosine_similarity.py
│   │   ├── create_user.py # Скрипт для создания пользователей
│   │   └── database.db # База данных SQLite
├── templates/ # Шаблоны HTML
│   ├── add_record.html # Шаблон для добавления записи
│   ├── admin_login.html # Шаблон для входа администратора
│   ├── admin_panel.html # Шаблон панели администратора
│   ├── base.html # Базовый шаблон
│   └── edit_record.html # Шаблон для редактирования записи
├── app.py # Основной файл приложения Flask
├── database.db # База данных SQLite
├── databases.py # Скрипт для работы с базой данных
├── get_data.py # Скрипт для получения данных
├── models.py # Файл с моделями для базы данных
├── requirements.txt # Файл с зависимостями проекта
└── .gitignore # Список файлов и директорий, игнорируемых Git
```