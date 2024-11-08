# TaskManager

Этот проект разворачивает веб-приложение для управления заметками, которое поддерживает регистрацию и авторизацию пользователей, а также предоставляет CRUD функционал для работы с заметками. Каждый пользователь имеет доступ только к своим заметкам.


## Установка и запуск
```bash
docker-compose up -d
```
## Структура проекта

- **Backend:** Java + Spring Framework
- **Frontend:** React + Bootstrap 5
- **Сервис шифрования:** Шифрование ГОСТ 28147-89 в виде отдельного сервиса
- **База данных:** PostgreSQL (добавлен pgAdmin для удобства управления)

## Компоненты

### Backend

- **Описание:** Реализован на Java с использованием Spring Framework.
- **Порт:** 8080
- **CORS:** Настроена политика CORS для взаимодействия с фронтендом.
  
#### Переменные окружения:

- `SPRING_DATASOURCE_URL`: URL подключения к БД, например `jdbc:postgresql://postgres:5432/web`
- `ENCRYPT_URL`: Адрес сервиса шифрования, например `http://encrypt:5000`
- `FRONT_URL`: Адрес фронтенда, например `http://127.0.0.1:3000`
- `KEY`: Ключ для шифрования, например `9f2d34a1b7c8e0ff2a4e6b12f9d0cba3`
- `SPRING_DATASOURCE_USERNAME`: Имя пользователя для БД, например `postgres`
- `SPRING_DATASOURCE_PASSWORD`: Пароль для БД, например `postgres`

#### Ссылки:

[Исходный код Backend](https://github.com/Minby93/webTask)

### Frontend

- **Описание:** Создан на React с использованием Bootstrap 5.
- **Адрес:** Доступ к приложению через `http://127.0.0.1:3000/login`

#### Переменные окружения:

- `REACT_APP_BACK_URL`: URL для взаимодействия с бэкендом, например `http://back:8080`
- `REACT_APP_LOGIN_BACK_URL`: URL для авторизации через Spring Security, например `http://back:8080/login`

> **Примечание:** Перед использованием приложения необходимо зарегистрироваться.

#### Ссылки:

[Исходный код Frontend](https://github.com/Minby93/webTaskFront)

### Сервис шифрования

- **Описание:** Реализовано шифрование ГОСТ 28147-89.

#### Ссылки:

[Исходный код сервиса шифрования](https://github.com/Minby93/EncryptService)

### PostgreSQL + pgAdmin

- **Описание:** PostgreSQL используется в качестве основной базы данных. pgAdmin добавлен для удобного управления БД.
- **pgAdmin Адрес:** Доступен по `http://127.0.0.1:15432`

#### Переменные окружения:

- `POSTGRES_DB`: Название БД, например `web`
- `POSTGRES_USER`: Имя пользователя для БД, например `postgres`
- `POSTGRES_PASSWORD`: Пароль для БД, например `postgres`
- `PGADMIN_DEFAULT_EMAIL`: Логин для pgAdmin, например `admin@pgadmin.com`
- `PGADMIN_DEFAULT_PASSWORD`: Пароль для pgAdmin, например `password`

#### Настройка pgAdmin:

1. Перейдите на `http://127.0.0.1:15432` и войдите, используя учетные данные.
2. Нажмите **Add New Server** и укажите имя.
3. Во вкладке **Connection** заполните данные, как показано на скриншоте, используя пароль `postgres` (если изменяли логин/пароль, укажите свои данные).
4. Разверните структуру базы данных и выберите **View/Edit Data** для нужной таблицы, чтобы просмотреть содержимое таблиц.

![pgAdmin настройки](https://github.com/user-attachments/assets/bb7b86cf-7778-4efe-bb3d-e4f5b55cc434)

![Структура таблиц](https://github.com/user-attachments/assets/4d14b0c3-6d8f-474e-9944-4e0701bf5f80)
