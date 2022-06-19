<p align="center">
  <img width="250" height="105" src="chatire-frontend/src/assets/logotype.png">
</p>


- [1. chatire](#1-chatire)
  - [1.1. Running the code](#11-running-the-code)
    - [1.1.1. Vue](#111-vue)
    - [1.1.2. Django](#112-django)
    - [1.1.3. RabbitMQ](#113-rabbitmq)
    - [1.1.4. WebSocket server](#114-websocket-server)

# 1. chatire

Real time Chat application built with Vue, Django, RabbitMQ and uWSGI WebSockets.

![chatire gif demo](./chatire.gif)

This repo contains the code for my tutorial **[Realtime django: Build a Chat application with Django, RabbitMQ and Vue.js](docs/part1.md)**

The tutorial is split into several parts:

- Part 1: [Introduction and Setup](docs/part1.md)
- Part 2: [Authentication and User Management](docs/part2.md)
- Part 3: [Build an API with django rest framework](docs/part3.md)
- Part 4 [Plug the Vue frontend to the django API](docs/part4.md)
- Part 5 [uWSGI WebSockets](docs/part5.md)
- Part 6 [Extras](docs/part6.md)

## 1.1. Running the code

### 1.1.1. Vue

Navigate to the `chatire-frontend directory`:

```bash
cd chatire-frontend
```

Install the dependencies from npm:

``` bash
npm install
```

Run the webpack dev server (starts on localhost:8080):

```bash
npm run dev
```

### 1.1.2. Django

To get the Django server running:

Install the requirements from pip

```bash
pip install -r requirements.txt
```

Run django's development server (starts on localhost:8000):

```bash
python manage.py runserver
```

### 1.1.3. RabbitMQ

Chatire uses RabbitMQ to bridge the django application and the uWSGI WebSocket server. The installation process varies. Check the [docs](https://www.rabbitmq.com/download.html) on how you can install it for your platform.

### 1.1.4. WebSocket server

Chatire uses `uWSGI` as it's websocket server, if you've already installed the requirements from `requirements.txt` if should already be installed.

You can start it with

```bash
uwsgi --http :8081 --gevent 100 --module websocket --gevent-monkey-patch --master
```

This starts uwsgi with 100 gevent (greenlet) threads. You can increase it if you want to.
