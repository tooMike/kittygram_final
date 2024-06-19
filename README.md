# Описание

Проект Kittygram позволяет пользователям делиться фотографиями своих котиков и хваститься их достижениями

Запущенный проект с тестовыми данными доступен по адресу: 

Документация к API достпуна по адресу: 

# Авторы проекта

[Mikhail](https://github.com/tooMike)

# Установка и запуск с Docker

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/tooMike/kittygram_final
```

```
cd kittygram_final
```

Запустить сборку проекта:

```
docker compose up
```

Выполнить сбор статики в контейнере backend:

```
docker compose exec backend python manage.py collectstatic
```

Выполнить миграции в контейнере backend:

```
docker compose exec backend python manage.py migrate
```

Проект будет доступен по адресу

```
http://127.0.0.1:9000/
```

# Спецификация

При локальном запуске документация будет доступна по адресу:

```
http://127.0.0.1:9000/redoc/ или http://127.0.0.1:9000/swagger/
```

# Основные технические требования

Python==3.9

# Примеры запросов к API

### Регистрация нового пользователя

Описание метода: Зарегистрировать пользователя в сервисе. Права доступа: Доступно без токена.

Тип запроса: `POST`

Эндпоинт: `/api/users/`

Обязательные параметры: `email, username, password`

Пример запрос:

```
{
  "email": "user@example.com",
  "username": "string",
  "password": "string"
}
```

Пример успешного ответа:

```
{
  "email": "user@example.com",
  "username": "string",
  "id": 0,
  "password": "string"
}
```

### Cписок котиков

Описание метода: Получение списка котиков. Права доступа: Аутентифицированные пользователи.

Тип запроса: `GET`

Эндпоинт: `/api/cats/`

Пример запроса:

Пример успешного ответа:

```
{
  "count": 0,
  "next": "http://example.com",
  "previous": "http://example.com",
  "results": [
    {
      "id": 0,
      "name": "string",
      "color": "string",
      "birth_year": -2147483648,
      "achievements": [
        {
          "id": 0,
          "achievement_name": "string"
        }
      ],
      "owner": 0,
      "age": "string",
      "image": "http://example.com",
      "image_url": "string"
    }
  ]
}
```

### Добавление нового котика

Описание метода: Добавить нового котика. Права доступа: Аутентифицированные пользователи.

Тип запроса: `POST`

Эндпоинт: `/api/cats/`

Обязательные параметры: `name, colour, birth_year`

Необязательные параметры: `achievements`

Пример запроса:

```
{
  "name": "string",
  "color": "string",
  "birth_year": -2147483648,
  "achievements": [
    {
      "achievement_name": "string"
    }
  ]
}
```

Пример успешного ответа:

```
{
  "id": 0,
  "name": "string",
  "color": "string",
  "birth_year": -2147483648,
  "achievements": [
    {
      "id": 0,
      "achievement_name": "string"
    }
  ],
  "owner": 0,
  "age": "string",
  "image": "http://example.com",
  "image_url": "string"
}
```