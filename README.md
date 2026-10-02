# pz3-http (PZ3)

Простой HTTP API задач на стандартной библиотеке `net/http`: in-memory хранилище, JSON-ответы и middleware-логирование.

## Запуск

```bash
go run ./cmd/server
```

Сборка:

```bash
go build -o ./bin/server ./cmd/server
./bin/server
```

## Маршруты

| Метод | Путь | Описание |
|-------|------|----------|
| GET | `/health` | `{"status":"ok"}` |
| GET | `/tasks` | список задач, фильтр `?q=` |
| POST | `/tasks` | создать задачу `{"title":"..."}` |
| GET | `/tasks/{id}` | получить задачу по id |

Примеры запросов: [requests.md](requests.md).

## Структура

```text
pz3-http/
  cmd/server/main.go
  internal/api/handlers.go
  internal/api/middleware.go
  internal/api/responses.go
  internal/storage/memory.go
  go.mod
  requests.md
  README.md
```
