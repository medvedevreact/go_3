# Тестовые запросы для PZ3

Базовый запуск сервера:

```bash
cd ~/Downloads/pz3-http
go run ./cmd/server
```

## 1. Health

```bash
curl -i http://localhost:8080/health
```

Ожидание: `200` и `{"status":"ok"}`.

## 2. Создать задачу

```bash
curl -i -X POST http://localhost:8080/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":"Купить молоко"}'
```

Ожидание: `201 Created` и JSON с `id`.

## 3. Список задач

```bash
curl -i http://localhost:8080/tasks
```

## 4. Фильтр по названию

```bash
curl -i "http://localhost:8080/tasks?q=молоко"
```

## 5. Получить задачу по id

```bash
curl -i http://localhost:8080/tasks/1
```

## 6. Ошибка: пустой title

```bash
curl -i -X POST http://localhost:8080/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":""}'
```

Ожидание: `400 Bad Request`.

## 7. Ошибка: неверный id

```bash
curl -i http://localhost:8080/tasks/abc
```

Ожидание: `400 Bad Request`.

## 8. Ошибка: задача не найдена

```bash
curl -i http://localhost:8080/tasks/9999
```

Ожидание: `404 Not Found`.
