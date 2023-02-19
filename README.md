# Team training project: api_yamdb - service that collects user feedback on works of art.

## GITHub action status:
![API_YAMDB workflow](https://github.com/damarkevich/yamdb_final/actions/workflows/yamdb_workflow/badge.svg)

## Technologies used:
Python3, Django Framework, Django Rest Framework, MySQL, JWT, docker

## Project description:

The YaMDb project collects user feedback on works of art. The works themselves are not stored in YaMDb; you cannot watch a movie or listen to music here.

The works are divided into categories such as "Books", "Films", "Music". For example, in the category "Books" there may be works "Winnie the Pooh and All-All-All" and "The Martian Chronicles", and in the category "Music" - the song "Yesterday" by the group "Beetles" and the second suite of Bach. The list of categories can be expanded (for example, you can add the category "fine art" or "jewellery").

A work can be assigned a genre from the predefined list (for example, Fairy Tale, Rock or Arthouse).
Only the administrator can add works, categories and genres.

Grateful or indignant users leave text reviews for the works and rate the work in the range from one to ten (an integer); from user ratings, an average rating of the work is formed - rating (integer). A user can leave only one review per work.

Only authenticated users can add reviews, comments and rate.

The project is accessed via API.

The project is pack into a docker container.

When uploading to GitHub, GitHub actions starting: The project image is automatically collected and sent to the DockerHub. Next, this image is deploing and starting on the server. If these tasks are successfully completed, the telegram bot receives a message about the completion of the procedure. 

To use this feature you need to fill secrets section in GitHub actions: DB_ENGINE, DB_NAME, POSTGRES_USER, POSTGRES_PASSWORD, DB_HOST, DB_PORT, HOST, DOCKER_USERNAME, DOCKER_PASSWORD, USER, SSH_KEY, PASSPHRASE, TELEGRAM_TO, TELEGRAM_TOKEN 


## How to launch a project:

Clone the repository and switch to it on the command line:

```
https://github.com/Damarkevich/yamdb_final
```

```
cd yamdb_final/infra
```

Create and fill .env file according to sample ".env.example":

```
cp .env.example .env
```
```
nano .env 
```

Create and run docker-compose container:

```
docker-compose up
```

Make migrations:

```
docker-compose exec web python manage.py makemigrations
```

Run migrations:

```
docker-compose exec web python manage.py migrate
```

Create superuser:

```
docker-compose exec web python manage.py createsuperuser
```

Collect static:

```
docker-compose exec web python manage.py collectstatic --no-input 
```

Project reacheble at:

```
http://localhost/
```


## Endpoints API YaMDb
```
auth: authentication.
```
```
users: users.
```
```
titles: works that are reviewed (a certain film, book or song).
```
```
categories: categories (types) of works ("Films", "Books", "Music").
```
```
genres: genres of works. One work can be tied to several genres.
```
```
reviews: reviews of works. Review is tied to a specific work.
```
```
comments: comments on reviews. Comment is tied to a specific review.
```
Each resource is described in the documentation on Russian: endpoints (addresses where you can make a request), allowed types of requests, access rights and additional parameters, if necessary, are indicated.

The documentation is available at:

```
http://localhost/redoc/
```

## .ENV example:

```
SECRET_KEY=
DB_ENGINE=
DB_NAME=
POSTGRES_USER=
POSTGRES_PASSWORD=
DB_HOST=
DB_PORT=
```

## Project Team

```
Tatyana Kutzenko
https://github.com/easyRU
```

```
Alexandr Sazonov
https://github.com/OnepunchZone
```

```
Dmitrii Markevich - Teamlead
github: https://github.com/Damarkevich/
```