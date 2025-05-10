# Docker-сборка для Cloud File Storage (Backend/Frontend)

## Структура проекта

- `backend` - подробнее [здесь](https://github.com/albakov/go-cloud-file-storage).
- `frontend` - подробнее [здесь](https://github.com/albakov/vue-cloud-file-storage).
- `docker` - volumes для mariadb, minio.

### Dev-стенд

MySQL - `docker/mariadb/data_test`

Minio - `docker/minio/data_test`

Env: `.env.dev`, `backend/.env.dev`

Docker-compose: `docker-compose.dev.yml`, `backend/docker-compose.dev.yml`

### Prod-стенд

MySQL - `docker/mariadb/data`

Minio - `docker/minio/data`

Env: `.env.prod`, `backend/.env.prod`

Docker-compose: `docker-compose.prod.yml`, `backend/docker-compose.prod.yml`

## Сборка проекта

Сначала переименуйте:

- .env.dev.example --> .env.dev
- .env.prod.example --> .env.prod

И в директории `backend`:

- .env.dev.example --> .env.dev
- .env.prod.example --> .env.prod

### Запуск dev-сборки:

```
docker compose -f docker-compose.yml -f docker-compose.dev.yml --env-file .env.dev --env-file backend/.env.dev up -d
```

### Запуск prod-сборки:

```
docker compose -f docker-compose.yml -f docker-compose.prod.yml --env-file .env.prod --env-file backend/.env.prod up -d
```

#### Nginx

Фронтенд будет доступен по адресу `http://localhost`. Изменить домен можно в `frontend/nginx.conf`, выставив новое значение для `server_name` и перезапустив сборку.

