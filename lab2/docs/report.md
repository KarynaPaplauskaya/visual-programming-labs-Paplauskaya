# Лабораторная работа №2. Node-RED

**Студент:** Поплавская Карина  
**Дата:** 16.10.2026

---

## 1. Краткое описание выполненного

В рамках лабораторной работы №2 был освоен Node-RED как low-code инструмент визуального программирования. Работа выполнялась в Docker-контейнере `mynodered` с сохранением данных в volume `node-red-data`, что позволяет потокам и файлам переживать перезапуски контейнера.

Реализованы следующие потоки (нажмите на название скриншота, чтобы открыть его):

| № | Flow | JSON-файл | Скриншот |
|---|---|---|---|
| 2.1 | Inject → Debug | `flow-01-inject-debug.json` | [01-inject-debug.png](../screenshots/01-inject-debug.png) |
| 2.2 | Function node | `flow-02-function.json` | [02-function.png](../screenshots/02-function.png) |
| 2.3 | Switch node | `flow-03-switch.json` | [03-switch.png](../screenshots/03-switch.png) |
| 2.4 | Change / Set node | `flow-04-change.json` | [04-change.png](../screenshots/04-change.png) |
| 2.5 | Template node | `flow-05-template.json` | [05-template.png](../screenshots/05-template.png) |
| 2.6 | HTTP Request node | `flow-06-http-request.json` | [06-http-request.png](../screenshots/06-http-request.png) |
| 2.7 | MQTT с публичным брокером | `flow-07-mqtt.json` | [07-mqtt.png](../screenshots/07-mqtt.png) |
| 2.8 | GET-эндпоинты | `flow-08-endpoints.json` | [08-endpoints.png](../screenshots/08-endpoints.png) |
| 2.9 | Dashboard с gauge и графиком | `flow-09-dashboard.json` | [09-dashboard.png](../screenshots/09-dashboard.png) |
| 2.10 | Telegram-бот | `flow-10-telegram.json` | [10-telegram.png](../screenshots/10-telegram.png) |
| 2.11 | Чтение и запись файла | `flow-11-files.json` | [11-files.png](../screenshots/11-files.png) |
| 2.12 | Работа с контекстом | `flow-12-context.json` | [12-context.png](../screenshots/12-context.png) |

---

## 2. Использованные AI-промпты

Примеры ключевых запросов к AI (ChatGPT) в ходе работы:

1. «Как запустить Node-RED в Docker с сохранением данных через volume и портом 1880?»
2. «Сгенерируй код function node для Node-RED, использующий let/const, if/else, цикл for, массив и объект, возвращающий объект с полем payload.»
3. «Как настроить switch node в Node-RED, чтобы ветвление шло по msg.payload.original > 10 и otherwise?»
4. «Как создать GET-эндпоинт в Node-RED с path-параметром :id и возвращать 200 / 400 / 404?»
5. «Как установить node-red-dashboard и настроить gauge + chart для имитации датчика температуры?»
6. «Как создать Telegram-бота через BotFather и подключить его к Node-RED через node-red-contrib-telegrambot?»
7. «Как в Node-RED писать и читать файл внутри Docker-контейнера через /data?»

---

## 3. Освоенные ноды

- **common:** `inject`, `debug`
- **function:** `function`, `switch`, `change`, `template`
- **network:** `http in`, `http response`, `http request`, `mqtt in`, `mqtt out`
- **storage:** `file`
- **dashboard:** `gauge`, `chart`, `ui_tab`, `ui_group`
- **telegrambot:** `telegram receiver`, `telegram command`, `telegram sender`
- **context:** flow context, global context

---

## 4. Способ установки и версии

**Способ установки:** Docker Desktop (Windows).

- Образ: `nodered/node-red:latest`
- Контейнер: `mynodered`
- Порт: `1880`
- Volume: `C:\Users\karin\Documents\node-red-data` → `/data`

**Версии:**

```
Node-RED version: v5.0.8
Node.js  version: v24.21.0
Docker Desktop version: v4.94.0
```

Версии Node-RED и Node.js можно узнать из логов контейнера:

```powershell
docker logs mynodered
```

Первые строки вывода содержат:

```
Welcome to Node-RED
===================
16 Oct 09:44:35 - [info] Node-RED version: v5.0.8
16 Oct 09:44:35 - [info] Node.js  version: v24.21.0
```

---

## 5. Скриншоты всех flow

Все скриншоты находятся в папке `lab2/screenshots/`. Нажмите на название файла, чтобы открыть скриншот:

| Файл | Что показывает |
|---|---|
| [00-versions.png](../screenshots/00-versions.png) | Версии Node-RED и Node.js |
| [01-inject-debug.png](../screenshots/01-inject-debug.png) | Flow 2.1 — inject → debug |
| [02-function.png](../screenshots/02-function.png) | Flow 2.2 — function node |
| [03-switch.png](../screenshots/03-switch.png) | Flow 2.3 — switch node |
| [04-change.png](../screenshots/04-change.png) | Flow 2.4 — change node |
| [05-template.png](../screenshots/05-template.png) | Flow 2.5 — template node |
| [06-http-request.png](../screenshots/06-http-request.png) | Flow 2.6 — http request |
| [07-mqtt.png](../screenshots/07-mqtt.png) | Flow 2.7 — MQTT publish/subscribe |
| [08-endpoints.png](../screenshots/08-endpoints.png) | Flow 2.8 — GET-эндпоинты |
| [09-dashboard.png](../screenshots/09-dashboard.png) | Flow 2.9 — dashboard (gauge + chart) |
| [10-telegram.png](../screenshots/10-telegram.png) | Flow 2.10 — Telegram-бот |
| [11-files.png](../screenshots/11-files.png) | Flow 2.11 — чтение/запись файла |
| [12-context.png](../screenshots/12-context.png) | Flow 2.12 — работа с контекстом |

---

## 6. Выводы

В ходе лабораторной работы я освоила Node-RED как low-code платформу для визуального программирования потоков данных. Поняла, как соединять ноды, передавать сообщения через `msg`, использовать поля `msg.payload`, `msg.topic`, `msg.req` и другие.

Отдельно разобралась с:

- **Function node** — написание JavaScript-кода с использованием массивов, объектов, циклов и условий.
- **Switch node** — ветвление потока по значению поля.
- **Change / Template** — модификация полей сообщения и формирование текста или JSON по шаблону Mustache.
- **HTTP Request** — получение данных с публичных API.
- **MQTT** — публикация и подписка через публичный брокер `broker.hivemq.com`.
- **HTTP-эндпоинты** — создание REST API прямо в Node-RED с разными статусами (200/400/404).
- **Dashboard** — визуализация данных в реальном времени (gauge, chart).
- **Telegram-бот** — интеграция с внешним сервисом через токен BotFather.
- **Файлы** — чтение и запись с сохранением данных между перезапусками контейнера.
- **Контекст** — хранение состояния между сообщениями.

Node-RED оказался удобным инструментом для быстрого прототипирования IoT- и API-решений: минимум кода, максимум наглядности. Docker с volume — надёжный способ запуска, при котором данные не теряются при перезапуске.

---

## 7. Ссылки

- Репозиторий: [github.com/KarynaPaplauskaya/visual-programming-labs-Paplauskaya](https://github.com/KarynaPaplauskaya/visual-programming-labs-Paplauskaya)
- Node-RED: [nodered.org](https://nodered.org)
- Docker: [docker.com](https://www.docker.com)
