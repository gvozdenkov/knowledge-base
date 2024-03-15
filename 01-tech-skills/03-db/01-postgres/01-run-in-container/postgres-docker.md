# Postgres with docker

## Просто запуск одного контейнера

1. Скачать нужный образ с докер хаба

```bash
docker pull postgres:14.3-alpine
```

2. Запустить контейнер

```bash
docker run -p 5432:5432 --rm --name postgres-test -u POSTGRES_USER=admin -e POSTGRES_PASSWORD=root -d postgres:14.3-alpine
```

3. Подключиться к контейнеру и к базе как дефолтный юзер `psql -U postgres` и активируем терминал `psql`

```bash
docker exec -it postgres-test psql -U postgres

# output
psql (14.3)
Type "help" for help.

postgres=#
```
