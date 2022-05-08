# api_final

## Описание:
api final - это REST API для блог-платформы Yatube. Позволяет просматривать и отправлять посты, просматривать группы, подписываться на авторов.

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/Maliarda/api_final_yatube.git
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python -m venv venv
```

```
source venv/Scripts/activate 
```

Установить зависимости из файла requirements.txt:

```
python -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python manage.py migrate
```

Запустить проект:

```
python manage.py runserver
```
## Примеры запросов:
### Запрос JWT токена с использованием логина и пароля пользователя SneakyFox:
```
  [POST].../api/v1/jwt/create/
  {
    "username": "SneakyFox",
    "password": "1234567bb"
}
```
### Ответ:
```
{"refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTY1MjA5NTYwNywianRpIjoiMDBmMGI0MG.sE5Bd3vrnQLIAL5GxxFg36tPoYyB9I5MQBE_iGshpK4",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjUyMDk1NjA3LCJqdGkiOiI0YmIxN2MzODcwNGU0YzQ0OWQ4Nzg4NzA4ODcyZTliMCIsInVzZXJfaWQiOjF9"
}
```
### Запрос с использованием токена пользователя SneakyFox для публикации поста:
```
    [POST].../api/v1/posts/
    {
    "text": "Фе́нек — миниатюрная лисица с крупными относительно тела ушами, живущая в пустынях Северной Африки. Иногда её относят к особому роду Fennecus. Имя зверёк получил от арабского слова فَنَك, что на одном из диалектов означает «лиса».",
    "group": 1   
    }
```

### Ответ:
```
{
    "id": 2,
    "text": "Фе́нек — миниатюрная лисица с крупными относительно тела ушами, живущая в пустынях Северной Африки. Иногда её относят к особому роду Fennecus. Имя зверёк получил от арабского слова فَنَك, что на одном из диалектов означает «лиса».",
    "author": "SneakyFox",
    "image": null,
    "group": 1,
    "pub_date": "2022-05-08T11:48:48.782688Z"
}
```
### Запрос для просмотра групп анонимным пользователем:
```
    [GET].../api/v1/groups/
```
### Пример ответа:
```
    [
    {
        "id": 1,
        "title": "Клуб любителей лисичек",
        "slug": "foxlovers",
        "description": "Фыр фыр фыр"
    },
    {
        "id": 2,
        "title": "Котолюбители",
        "slug": "catslovers",
        "description": "Мур ^^"
    }
]
```

### Подробная документация в формате ReDoc доступна по адресу .../redoc/