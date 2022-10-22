# Описание 

### API-сервис для соц.сети блогеров.

## Особенности:

- система регистрации и аутентификации пользователей
- разделение прав доступа: аноним, пользователь, администратор
- редактирование опубликованных постов
- добавление комментариев
- подписка на понравившихся авторов

## Применяемые в проекте технологии:

- Django
- Django Rest Framework
- GIT
- Python
- JWT

# Как запустить проект:

- Клонировать репозиторий и перейти в него в командной строке:

``` git clone https://github.com/Alekc29/api_final_yatube.git ```

``` cd api_final_yatube ```

- Cоздать и активировать виртуальное окружение:

``` python3 -m venv env ```

``` source env/bin/activate ```

- Установить зависимости из файла requirements.txt:

``` python3 -m pip install --upgrade pip ```

``` pip install -r requirements.txt ```

- Выполнить миграции:

``` python3 manage.py migrate ```

- Запустить проект:

``` python3 manage.py runserver ```

# Примеры


### Создание поста(/api/v1/posts/) (POST): пример запроса:
```
{
  "text": "string",
  "image": "string",
  "group": 0
}
```
- пример ответа 201:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}
```
- пример ответа 400:
```
{
  "text": [
    "Обязательное поле."
  ]
}
```
- пример ответа 401:
```
{
  "detail": "Учетные данные не были предоставлены."
}
```
### Получение постов(/api/v1/posts/)(GET): пример ответа:
```
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 0
    }
  ]
}
```
### Получение поста (/api/v1/posts/{id}/)(GET): пример ответа 200:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}
```
- пример ответа 404:
```
{
  "detail": "Страница не найдена."
}
```
### Обновление и частичное обновление поста (/api/v1/posts/{id}/)(PUT, PATCH): пример запроса:
```
{
  "text": "string",
  "image": "string",
  "group": 0
}
```
- пример ответа 200:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}
```
- пример ответа 400:
```
{
  "text": [
    "Обязательное поле."
  ]
}
```
- пример ответа 401:
```
{
  "detail": "Учетные данные не были предоставлены."
}
```
- пример ответа 403:
```
{
  "detail": "У вас недостаточно прав для выполнения данного действия."
}
```
- пример ответа 404:
```
{
  "detail": "Страница не найдена."
}
```
### Удаление поста(DELETE): пример ответа 401:
```
{
  "detail": "Учетные данные не были предоставлены."
}
```
- пример ответа 403:
```
{
  "detail": "У вас недостаточно прав для выполнения данного действия."
}
```
- пример ответа 404:
```
{
  "detail": "Страница не найдена."
}
```
### Получение комментариев (/api/v1/posts/{post_id}/comments/)(GET): пример ответа:
```
[
  {
    "id": 0,
    "author": "string",
    "text": "string",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
  }
]
```
### Добавление комментариев (/api/v1/posts/{post_id}/comments/)(POST): пример запроса:
```
{
  "text": "string"
}
```
- пример ответа 201:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}
```
- пример ответа 400:
```
{
  "text": [
    "Обязательное поле."
  ]
}
```
- пример ответа 401:
```
{
  "detail": "Учетные данные не были предоставлены."
}
```
- пример ответа 404:
```
{
  "detail": "Страница не найдена."
}
```
### Получение комментария (/api/v1/posts/{post_id}/comments/{id}/)(GET): пример ответа:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}
```
### Обновление и частичное обновление комментария (/api/v1/posts/{post_id}/comments/{id}/)(PUT, PATCH): пример запроса:
```
{
  "text": "string"
}
```
- пример ответа:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}
```
### Удаление комментария (/api/v1/posts/{post_id}/comments/{id}/)(DELETE): пример ответа:
```
{
  "detail": "Учетные данные не были предоставлены."
}
```
### Список групп (/api/v1/groups/)(GET): пример ответа:
```
[
  {
    "id": 0,
    "title": "string",
    "slug": "string",
    "description": "string"
  }
]
```
### Информация о группе (/api/v1/groups/{id}/)(GET): пример ответа:
```
[
  {
    "id": 0,
    "title": "string",
    "slug": "string",
    "description": "string"
  }
]
```
### Подписки (/api/v1/follow/)(GET): пример ответа:
```
[
  {
    "user": "string",
    "following": "string"
  }
]
```
### Подписка(/api/v1/follow/)(POST): пример запроса:
```
{
  "following": "string"
}
```
- пример ответа:
```
{
  "user": "string",
  "following": "string"
}
```
### Получить JWT-токен (/api/v1/jwt/create/)(POST): пример запроса:
```
{
  "username": "string",
  "password": "string"
}
```
- пример ответа:
```
{
  "refresh": "string",
  "access": "string"
}
```
### Обновить JWT-токен (/api/v1/jwt/refresh/)(POST): пример запроса:
```
{
  "refresh": "string"
}
```
- пример ответа:
```
{
  "access": "string"
}
```
### Проверить JWT-токен (/api/v1/jwt/verify/)(POST): пример запроса:
```
{
  "token": "string"
}
```
- пример ответа:
```
{
  "token": [
    "Обязательное поле."
  ]
}
```