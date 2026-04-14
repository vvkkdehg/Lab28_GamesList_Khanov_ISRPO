# Лабораторная работа №28. Веб-сервер на C#: список любимых игр с полным управлением

## Описание проекта

Веб-сервер на ASP.NET Core, который позволяет управлять списком любимых игр. Сервер поддерживает полный CRUD (Create, Read, Update, Delete) через HTTP-методы GET, POST, PUT и DELETE.

## Инструкция по запуску
1. Перейдите в папку проекта: cd GamesApi
2. Восстановите зависимости: dotnet restore
3. Запустите сервер: dotnet run
4. Запомните порт из вывода терминала (например http://localhost:5101)
5. Откройте новый терминал и отправьте запрос: curl http://localhost:5101/api/games
6. Остановите сервер комбинацией Ctrl + C

## Таблица маршрутов
| Метод | Маршрут | Описание | Статус |
|-------|---------|----------|--------|
| GET | `/api/games` | Получить все игры | 200 |
| GET | `/api/games/{id}` | Получить игру по id | 200 / 404 |
| POST | `/api/games` | Добавить игру | 201 |
| DELETE | `/api/games/{id}` | Удалить игру | 204 / 404 |

## Примеры curl команд
- GET /api/games — получить все игры
  ```bash
  curl http://localhost:5101/api/games
  ```

- GET /api/games/{id} — получить игру по id
  ```bash
  curl http://localhost:5101/api/games/1
  ```

- GET /api/games/favourites — получить избранные игры
  ```bash
  curl http://localhost:5101/api/games/favourites
  ```

- POST /api/games — добавить новую игру
  ```bash
  curl -X POST http://localhost:5101/api/games -H "Content-Type: application/json" -d "{\"title\": \"Stardew Valley\", \"genre\": \"Simulation\", \"releaseYear\": 2016, \"isFavourite\": true}"
  ```

- PUT /api/games/{id} — обновить игру
  ```bash
  curl -X PUT http://localhost:5101/api/games/2 -H "Content-Type: application/json" -d "{\"title\": \"Witcher 3\", \"genre\": \"RPG\", \"releaseYear\": 2015}"
  ```

- DELETE /api/games/{id} — удалить игру
  ```bash
  curl -X DELETE http://localhost:5101/api/games/1
  ```

- DELETE /api/games/{id} — ошибка 404 (несуществующая игра)
  ```bash
  curl -X DELETE http://localhost:5101/api/games/99
  ```