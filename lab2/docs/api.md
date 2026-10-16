# API Documentation — Lab 2

Base URL: `http://localhost:1880`

---

## 1. GET /api/text

Возвращает простой текст.

**Запрос:**
```
GET http://localhost:1880/api/text
```

**Ответ (200, text/plain):**
```
Hello from Node-RED! Student: Paplauskaya
```

---

## 2. GET /api/info

Возвращает JSON-объект с информацией.

**Запрос:**
```
GET http://localhost:1880/api/info
```

**Ответ (200, application/json):**
```json
{
  "app": "Node-RED",
  "lab": 2,
  "student": "Paplauskaya",
  "time": "2026-10-16T12:34:56.789Z"
}
```

---

## 3. GET /api/items/:id

Возвращает элемент по идентификатору.

**Path parameter:**
- `:id` — целое число от 1 до 3

**Query parameter (необязательный):**
- `limit` — любая строка, отображается в ответе

### Пример успешного запроса

```
GET http://localhost:1880/api/items/2?limit=10
```

**Ответ (200, application/json):**
```json
{
  "id": 2,
  "name": "Item 2",
  "limit": "10",
  "timestamp": "2026-10-16T12:34:56.789Z"
}
```

### Пример ошибки 400 (id не число)

```
GET http://localhost:1880/api/items/abc
```

**Ответ (400, application/json):**
```json
{
  "error": "Bad Request",
  "message": "id must be a number",
  "received": "abc"
}
```

### Пример ошибки 404 (id вне диапазона)

```
GET http://localhost:1880/api/items/999
```

**Ответ (404, application/json):**
```json
{
  "error": "Not Found",
  "message": "item not found",
  "id": 999
}
```