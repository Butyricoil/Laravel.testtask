# Laravel Test Task

REST API для управления проектами и задачами. Laravel 12 + MySQL 9.1 + Docker.

## Установка

### 1. Настройка окружения
```bash
copy .env.example .env
```

Файл `.env` уже настроен для Docker. Основные параметры:
```env
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laraveltesktask
DB_USERNAME=root
DB_PASSWORD=root
```

### 2. Установка и Запуск
```bash
git clone https://github.com/Butyricoil/Laravel.testtask
docker-compose up -d --build
```

## Доступ

- API: http://localhost:8000/api
- phpMyAdmin: http://localhost:8080 (root/root)

## API Endpoints POSTMAN

| Метод | URL | Описание |
|-------|-----|----------|
| GET | `/api/projects` | Все проекты |
| POST | `/api/projects` | Создать проект |
| GET | `/api/projects/{id}` | Проект по ID |
| PUT | `/api/projects/{id}` | Обновить проект |
| DELETE | `/api/projects/{id}` | Удалить проект + задачи |
| GET | `/api/tasks` | Все задачи |
| POST | `/api/tasks` | Создать задачу |
| GET | `/api/tasks/{id}` | Задача по ID |
| PUT | `/api/tasks/{id}` | Обновить задачу |
| DELETE | `/api/tasks/{id}` | Удалить задачу |

## Тестирование через cURL

### Создать проект
```bash
curl -X POST http://localhost:8000/api/projects -H "Content-Type: application/json" -d "{\"name\":\"Project 1\",\"description\":\"Description\"}"
```

### Получить проекты
```bash
curl http://localhost:8000/api/projects
```

### Создать задачу
```bash
curl -X POST http://localhost:8000/api/tasks -H "Content-Type: application/json" -d "{\"project_id\":1,\"title\":\"Task 1\",\"status\":\"pending\",\"deadline\":\"2025-12-31\"}"
```

### Получить задачи
```bash
curl http://localhost:8000/api/tasks
```

### Удалить проект (каскадное удаление задач)
```bash
curl -X DELETE http://localhost:8000/api/projects/1
```

## Postman

Импортируйте `laraveltesktask.postman_collection.json` в Postman для готовых запросов.

## Структура данных

**Project:**
```json
{
  "id": 1,
  "name": "Project Name",
  "description": "Description",
  "tasks": []
}
```

**Task:**
```json
{
  "id": 1,
  "project_id": 1,
  "title": "Task Title",
  "status": "pending",
  "deadline": "2025-12-31"
}
```

**Статусы:** `pending`, `in_progress`, `completed`
