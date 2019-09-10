# Barge

> ⚠️ Work in progress

Barge provides you with dockerized environment to run your Laravel application.

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

Get in your `barge` folder:

```
cd barge
```

Prepare your `docker-compose.yml` and `.env` files:

```
cp docker-composer.yml.dist docker-compose.yml
cp .env.dist .env
```

Update your `.env` environment file to match your requirements:

```
vim .env
```

Add a `.dockerignore` file to your project root folder:

```
cp .dockerignore.dist ../.dockerignore
```

## Usage

Use the `barge` executable to manage your containers:

```
bin/barge help
```

### Stack

- maildev
- mongodb
- mysql
- redis
- nginx
- php-fpm
- php-worker
- php-scheduler
- workbench

---

## ToDo:
- Make & reuse own PHP image
- Write Dockerfile for the `workbench` container
- Add a `memcached` container
- Finalize bin/barge
- Update readme.md
- ...
