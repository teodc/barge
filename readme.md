# Barge

> ⚠️ This project is still a work in progress

Barge provides you a dockerized environment to run your PHP application.

## Requirements

- Docker
- Docker Compose
- Git

## Installation

From your app project folder, checkout Barge in a `barge` folder:

```
git clone https://github.com/teodc/barge.git barge
```

> Don't forget to add `/barge` to your project's `.gitignore` file.

Add the `docker-compose.yml` and `.dockerignore` files in your project directory:

```
cp barge/docker-composer.yml.dist docker-compose.yml
cp barge/.dockerignore.dist .dockerignore
```

Prepare an environment file from the `barge.env.dist`:

```
cp barge/barge.env.dist barge/barge.env
```

Update your `barge.env` environment file:

```
vim barge/barge.env
```

## Usage

Use the `barge` bash executable to

```
bin/barge help
```

### Stack

- app (WIP)
- maildev
- mongodb
- mysql
- nginx
- php-fpm
- php-queue-worker
- php-scheduler
- redis

---

## ToDo:
- Write Dockerfile for the `app` container
- Add a `memcached` container
- Finalize bin/barge
- Update readme.md
- Check docker-sync
- ...
