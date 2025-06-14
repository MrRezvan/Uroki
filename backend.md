# Техническое задание для проверки преподавателей по направлению «Бэкенд (Django)»

**Время на выполнение:** 35 минут

---

## 🎯 Цель задания

Проверить уровень владения ключевыми технологиями и навыками, соответствующими тем, которые преподаватели применяют в учебных проектах в течение года:

- Работа с моделями (`models.py`)
- Настройка маршрутов (`urls.py`)
- Создание представлений (`views.py`)
- Использование шаблонов (`templates`)
- Создание базового шаблона (`base.html`) и наследование от него
- Отображение данных из связанных моделей
- Использование Django admin для наполнения базы

> ⚠️ Задание не требует использования аутентификации пользователей, DRF, классов `ModelForm`, сигналов, middleware и других неосвоенных тем.

---

## 📌 Формулировка задания

**Название задания:** _Мини-соцсеть для питомцев_

Разработать базовую версию социальной сети, где пользователи могут публиковать посты от имени своих питомцев. Каждый питомец привязан к владельцу, а опубликованные посты могут получать лайки.

---

## ⚙️ Функциональные требования

### Модели (`models.py`)

Создать следующие модели:

#### `Pet`
- `name` — имя питомца (строка)
- `breed` — порода (строка)
- `owner_name` — имя владельца (строка)

#### `Post`
- `title` — заголовок поста
- `content` — текст поста
- `post_image` - картинка для поста
- `pet` — внешний ключ к модели `Pet`

#### `Like`
- `post` — внешний ключ к модели `Post`
- `user_identifier` — идентификатор пользователя (тип: строка; можно использовать IP-адрес)

---

### Представления (`views.py`)

- Страница со списком всех постов (`/posts/`):  
  Отображать:
  - заголовок поста
  - имя питомца
  - текст поста
  - картинку поста
  - количество лайков
  - кнопка "Поставить лайк"

- Обработка лайка:
  - По нажатию на кнопку пользователь может поставить лайк посту
  - Один и тот же пользователь не может лайкнуть один и тот же пост дважды

---


### Шаблоны (`templates/`)

- Использовать базовый шаблон `base.html` с блоками для наследования
- Создать шаблон страницы списка постов (`posts.html`)
- Разметка должна быть корректной и понятной  
  (использование Bootstrap **не требуется**)

---

## ⛔ Ограничения и условия

- **Авторизация не используется.**  
  Личность пользователя при лайке идентифицируется, например, по IP (`request.META.get('REMOTE_ADDR')`) или иным способом в рамках известных возможностей.

- **Лайк не должен дублироваться.**  
  Один "пользователь" не может лайкнуть один и тот же пост дважды. Это часть задания с усложнением и проверкой на внимательность.

- **Админка может использоваться для создания объектов.**  
  Реализация интерфейса создания постов и питомцев через сайт **не требуется**.

---

