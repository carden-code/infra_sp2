# Проект "Yamdb"

- Учебный проект для командной разработке API для веб приложения YaMDb, базируемых на фреймворке Django и модуле Django Rest Framework. Для обеспечения контороля прав доступа в проекте используется модуль JWT-токен.

## Описание проекта:

- Проект **YaMDb** собирает **отзывы** (**Review**) пользователей на **произведения** (**Titles**). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список **категорий** (**Category**) может быть расширен администратором (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).

- Сами произведения в **YaMDb** не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
- В каждой категории есть **произведения**: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха.

- Произведению может быть присвоен **жанр** (**Genre**) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.

- Благодарные или возмущённые пользователи оставляют к произведениям текстовые **отзывы** (**Review**) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — **рейтинг** (целое число). На одно произведение пользователь может оставить только один отзыв.

## Установка и запуск:

- Клонировать репозиторий и перейти в него в командной строке (используем ssh):

`git clone git@github.com:carden-code/infra_sp2.git
`
- Добавьте файл .env в котором хранится SECRET_KEY и настройки БД:

`cd infra_sp2/infra
`

```
echo "SECRET_KEY=YourSecretKey 
DB_ENGINE=django.db.backends.postgresql 
DB_NAME=postgres 
POSTGRES_USER=postgres 
POSTGRES_PASSWORD=postgres 
DB_HOST=db DB_PORT=5432" > .env
```
- Пример заполнения файла .env: 

```
SECRET_KEY=by8f8347h9hpwidjflahgkakglamdlfmsdjkbj
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql 
DB_NAME=postgres # имя базы данных 
POSTGRES_USER=postgres # логин для подключения к базе данных 
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой) 
DB_HOST=db # название сервиса (контейнера) 
DB_PORT=5432 # порт для подключения к БД 
```

- Cборка docker-compose:

`sudo docker-compose up
` 

`sudo docker-compose exec python manage.py makemigrations
`

`sudo docker-compose exec python manage.py migrate
`

`sudo docker-compose exec python manage.py createsuperuser
`

`sudo docker-compose exec python manage.py collectstatic
`
- Заполнение базы данными:

`sudo docker-compose exec python manage.py load_info
`

- Получаем ключ авторизации для получения токена:

`sudo docker-compose exec web bash
`

`cd send_emails
`

`cat "файл с почтой"
`

### Примеры использования API:

- Дитальное описание и примеры работы API проекта представлены в документации: http://127.0.0.1:8000/redoc/ в формате ReDoc. 

### Автор:
- #### [Борисенко Вячеслав](https://github.com/carden-code "Борисенко Вячеслав")

### Лицензия:
- Этот проект лицензируется в соответствии с лицензией MIT ![](https://miro.medium.com/max/156/1*A0rVKDO9tEFamc-Gqt7oEA.png "1")