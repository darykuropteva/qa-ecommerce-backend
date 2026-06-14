# 🧪 QA — E-Commerce Backend

> Manual testing of the e-commerce platform backend (REST API)

---

> Ручное тестирование бэкенда e-commerce платформы (REST API)

---

## 🇷🇺 О проекте

Данный репозиторий содержит артефакты ручного тестирования бэкенда интернет-магазина,
реализованного на Spring Boot с микросервисной архитектурой.

**Тестируемый проект:** [e-commerce-2/backend](https://github.com/e-commerce-2/backend)  

### Стек тестируемого приложения

| Компонент | Технология |
|---|---|
| Фреймворк | Spring Boot (Java) |
| Архитектура | Микросервисы + Eureka Service Discovery |
| База данных | PostgreSQL |
| Кэш | Redis |
| Аутентификация | JWT |
| Запуск | Docker / Docker Compose |

### Микросервисы

| Сервис | Порт | Описание |
|---|---|---|
| `api-gateway` | 8080 | Точка входа, роутинг |
| `user-service` | 8081 | Пользователи, аутентификация |
| `product-service` | 8082 | Каталог товаров, категории, склад |
| `cart-service` | 8083 | Корзина (Redis) |
| `order-service` | 8084 | Заказы |

---

## 🇬🇧 About

This repository contains manual testing artifacts for an e-commerce backend built
with Spring Boot microservices architecture.

**Project under test:** [e-commerce-2/backend](https://github.com/e-commerce-2/backend)  

### Tech Stack

| Component | Technology |
|---|---|
| Framework | Spring Boot (Java) |
| Architecture | Microservices + Eureka Service Discovery |
| Database | PostgreSQL |
| Cache | Redis |
| Auth | JWT |
| Deploy | Docker / Docker Compose |

---

## 📁 Структура репозитория / Repository Structure

```
qa-ecommerce-backend/
│
├── test-cases/                  # Тест-кейсы / Test cases
│   ├── admin-categories.md      # Управление категориями
│   ├── admin-products.md        # Управление товарами
│   ├── admin-orders.md          # Управление заказами
│   └── admin-roles.md           # Роли и доступ
│
├── bug-reports/                 # Сводная таблица багов / Bug summary
│   └── README.md
│
├── test-report/                 # Итоговый отчёт / Test report
│   └── admin-module-report.md

```

---

## 🔍 Область тестирования / Scope

### Протестированные модули / Tested modules

| Модуль | Сервис | Эндпоинты |
|---|---|---|
| Управление категориями | product-service :8082 | `POST/PUT/DELETE /api/categories` |
| Управление товарами | product-service :8082 | `POST/PUT/DELETE /api/products` |
| Управление складом | product-service :8082 | `POST/DELETE /api/stocks/*` |
| Управление заказами | order-service :8084 | `GET/PUT /api/admin/orders/*` |
| Роли и доступ | product-service, order-service | Admin vs User |

### Не вошло в скоуп / Out of scope

- Автоматизированное тестирование
- Нагрузочное тестирование
- Тестирование фронтенда
- Тестирование модулей в роли user (тестировались другими участниками команды)
  
---

## 🛠 Инструменты / Tools

| Инструмент | Использование |
|---|---|
| Postman | Выполнение API-запросов |
| Docker Desktop | Запуск тестового окружения (docker-compose.dev.yml) |
| PostgreSQL (psql) | Верификация данных в БД |
| Redis CLI | Проверка состояния кэша |
| GitHub Issues | Баг-трекинг |

---

## 📊 Итоги тестирования / Test Results

| Показатель | Значение |
|---|---|
| ✅ Всего проверок | **120** |
| 🟢 Пройдено успешно | **95** |
| 🔴 Упало (найдены дефекты) | **25** |
| ⏭️ Пропущено (skipped) | **0** |

📄 [Полный отчёт о тестировании](./test-report/admin-module-report.md)

---

## 🐛 Баг-репорты / Bug Reports

Все найденные дефекты оформлены как [GitHub Issues](https://github.com/darykuropteva/qa-ecommerce-backend/issues).

| Критичность | Количество | Описание |
|---|---|---|
| 🔴 Блокирующий | 1 | Невозможно изменить статус заказа администратором |
| 🟠 Критический | 1 | Невозможно отменить активную резервацию товара |
| 🟡 Высокий | 19 | Валидация, HTTP-статусы, бизнес-логика |
| **Итого** | **21** | BUG-ADMIN-1 — BUG-ADMIN-21 |

---

## ⚠️ Серые зоны / Grey Areas

В ходе тестирования выявлены места с неоднозначным поведением,
не задокументированным в требованиях:

| # | Вопрос | Статус |
|---|---|---|
| 1 | Минимальное значение `price` — 0.01 или 1.00? | ❓ Не задокументировано |
| 2 | Граф переходов статусов заказа | ❓ Не задокументировано |
| 3 | Поведение `availableStock` при уменьшении `totalStock` ниже `reservedStock` | ❓ Не задокументировано |
| 4 | Максимум `price` по ТЗ (99 999 999.99) vs ограничение БД `decimal(12,2)` | ❓ Конфликт |
| 5 | Валидация `description` товара — конфликт между схемой БД (5000) и валидацией API (500) | ❓ Конфликт |

---

## 💡 Предложения по улучшению / Improvement Suggestions

1. **Валидация поля `name`** — запретить значения только из цифр и спецсимволов
2. **Строгая схема для `price`** — валидация максимума, знаков после запятой, единый формат
3. **Улучшить обработку ошибок** — информативные сообщения вместо `"Что-то пошло не так"`
4. **Усилить валидацию типов** — `categoryId` только integer, `totalStock` только integer

---

## 🏁 Общий вывод / Conclusion

В ходе тестирования административного модуля выявлен **21 дефект**,
включая **1 блокирующий** и **1 критический**.

Основные проблемы: валидация входных данных, обработка ошибок,
корректность HTTP-статусов и бизнес-логика работы со складом и заказами.

Наиболее критичны:
- **BUG-ADMIN-21** — невозможность изменения статуса заказа администратором
- **BUG-ADMIN-15** — невозможность отмены активной резервации товара

> Текущая версия сервиса требует доработки и повторного регрессионного
> тестирования после исправления выявленных дефектов.

---

*Тестирование проводилось на локальном окружении (localhost) через docker-compose.dev.yml*  
*Testing was performed in a local environment via docker-compose.dev.yml*
