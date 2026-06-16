---
# Практическое задание 29

## ЭФМО-02-25 

## Алиев Каяхан Командар оглы
---
# Тема работы
Подключение к RabbitMQ. Отправка и получение сообщений

## Цели занятия
Научиться поднимать RabbitMQ, публиковать сообщения в очередь и обрабатывать их потребителем с подтверждением (ack), понимая основы надёжности доставки.

## Коды статуса:
-	200 OK — успешный ответ
-	201 Created — ресурс создан
-	204 No Content — успешно, без тела
-	400 Bad Request — неверные данные
-	404 Not Found — ресурс не найден
-	422 Unprocessable Entity — некорректные данные по смыслу
-	500 Internal Server Error — внутренняя ошибка

# Примечания по конфигурации и требования

Для запуска требуется:

Go: версия 1.25.1

<img width="841" height="232" alt="Установка Git и Go" src="https://github.com/user-attachments/assets/8e01d831-5a7f-4376-8348-9052b240aec9" />


# Команды запуска/сборки
## 1) Клонировать данный репозиторий в удобную для вас папку:
```Powershell
git clone https://github.com/kayahan81/pz29
```
## 2) Перейти в папку pz19:
```Powershell
cd pz29
```
## 3) Загрузка зависимостей:
```Powershell
go mod tidy
```
## 4) Команда запуска
В первом окне
```Powershell
go run 
```

# Проверка работоспособности
## Создать задачу (триггер события)
```Powershell
curl -X POST http://localhost:8082/v1/tasks \
  -H "Authorization: Bearer demo-token" \
  -H "Content-Type: application/json" \
  -H "X-Request-ID: rabbit-test-001" \
  -d '{"title":"RabbitMQ тест","description":"Проверка очереди","due_date":"2026-05-20"}'
```
## Создать несколько задач
```Powershell
curl -X POST http://localhost:8082/v1/tasks \
  -H "Authorization: Bearer demo-token" \
  -H "Content-Type: application/json" \
  -d '{"title":"Задача 1","due_date":"2026-05-20"}'

curl -X POST http://localhost:8082/v1/tasks \
  -H "Authorization: Bearer demo-token" \
  -H "Content-Type: application/json" \
  -d '{"title":"Задача 2","due_date":"2026-05-20"}'
```
