# API Yatube

## Описание

API Yatube обеспечивает взаимодействие с пользователями и основным контентом социальной платформы.

Все посетители имеют доступ к просмотру постов, сообществ и комментариев, а также могут оставлять отклики под существующими публикациями.

Зарегистрированные пользователи могут создавать новые записи, связывать их с определёнными сообществами, комментировать, подписываться на других участников.

Владельцы материалов обладают правами на изменение и удаление своих постов и комментариев, включая частичное редактирование.

---

## Зависимости

```
Django==3.2.16
pytest==6.2.4
pytest-pythonpath==0.7.3
pytest-django==4.4.0
djangorestframework==3.12.4
djangorestframework-simplejwt==4.7.2
Pillow==9.3.0
PyJWT==2.1.0
requests==2.26.0
djoser==2.1.0
```

---

## Как запустить проект

1. Клонировать репозиторий и перейти в него:

```bash
git clone https://github.com/DXVDMVN/api_final_yatube
cd yatube_api
```

2. Создать и активировать виртуальное окружение:

```bash
python3 -m venv env
source env/bin/activate
```

3. Установить зависимости:

```bash
python3 -m pip install --upgrade pip
pip install -r requirements.txt
```

4. Выполнить миграции:

```bash
python3 manage.py migrate
```

5. Запустить сервер:

```bash
python3 manage.py runserver
```

---

## Примеры запросов к API

### Получение токена для авторизованного пользователя

**POST** `/api/v1/jwt/create/`

```json
{
  "username": "user",
  "password": "user"
}
```

---

### Создание поста

**POST** `/api/v1/posts/`

```json
{
  "text": "Мой тестовый пост через Postman",
  "group": 1
}
```

**Ответ:**

```json
{
  "id": 5,
  "text": "Мой тестовый пост через Postman",
  "pub_date": "2025-06-13T18:40:19.675793Z",
  "author": "user",
  "image": null,
  "group": 1
}
```

---

### Получение всех постов

**GET** `/api/v1/posts/`

```json
[
  {
    "id": 4,
    "text": "Пост зарегистрированного пользователя.",
    "pub_date": "2025-06-13T18:19:30.096211Z",
    "author": "regular_user",
    "image": null,
    "group": null
  },
  {
    "id": 5,
    "text": "Мой тестовый пост через Postman",
    "pub_date": "2025-06-13T18:40:19.675793Z",
    "author": "user",
    "image": null,
    "group": 1
  }
]
```
