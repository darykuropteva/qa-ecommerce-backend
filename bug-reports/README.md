# 🐛 Баг-репорты / Bug Reports

Все дефекты найдены в ходе ручного тестирования модуля **Администрирование**.  
Период тестирования: 22.05.2026 — 30.05.2026  
Окружение: localhost, docker-compose.dev.yml

---

## Статистика / Summary

| Критичность | Количество |
|---|---|
| 🔴 Блокирующий | 1 |
| 🟠 Критический | 1 |
| 🟡 Высокий | 19 |
| **Итого** | **21** |

---

## Сводная таблица / Bug List

| ID | Issue | Название | Эндпоинт | Критичность | Статус |
|---|---|---|---|---|---|
| BUG-ADMIN-21 | [#1](https://github.com/darykuropteva/qa-ecommerce-backend/issues/1) | Невозможно обновить статус заказа с токеном админа | `PUT /api/admin/orders/{id}/status` | 🔴 Блокирующий | Open |
| BUG-ADMIN-15 | [#2](https://github.com/darykuropteva/qa-ecommerce-backend/issues/2) | Возвращает 400 при отмене резервации со статусом ACTIVE | `DELETE /api/stocks/reservations/{code}` | 🟠 Критический | Open |
| BUG-ADMIN-1 | [#3](https://github.com/darykuropteva/qa-ecommerce-backend/issues/3) | Создание категории с description 499-500 символов возвращает 400 | `POST /api/categories` | 🟡 Высокий | Open |
| BUG-ADMIN-2 | [#4](https://github.com/darykuropteva/qa-ecommerce-backend/issues/4) | Обновление категории с description 499-500 символов возвращает 400 | `PUT /api/categories/{id}` | 🟡 Высокий | Open |
| BUG-ADMIN-3 | [#5](https://github.com/darykuropteva/qa-ecommerce-backend/issues/5) | Создание товара с description 499-500 символов возвращает 400 | `POST /api/products` | 🟡 Высокий | Open |
| BUG-ADMIN-4 | [#6](https://github.com/darykuropteva/qa-ecommerce-backend/issues/6) | Неинформативное сообщение об ошибке при description > 500 символов | `POST /api/products` | 🟡 Высокий | Open |
| BUG-ADMIN-5 | [#7](https://github.com/darykuropteva/qa-ecommerce-backend/issues/7) | Отсутствует валидация максимального значения поля price | `POST /api/products` | 🟡 Высокий | Open |
| BUG-ADMIN-6 | [#8](https://github.com/darykuropteva/qa-ecommerce-backend/issues/8) | Некорректная обработка дробных значений в поле price | `POST /api/products` | 🟡 Высокий | Open |
| BUG-ADMIN-7 | [#9](https://github.com/darykuropteva/qa-ecommerce-backend/issues/9) | Неинформативное сообщение при передаче строки в поле price | `POST /api/products` | 🟡 Высокий | Open |
| BUG-ADMIN-8 | [#10](https://github.com/darykuropteva/qa-ecommerce-backend/issues/10) | Принимает дробное значение в поле categoryId | `POST /api/products` | 🟡 Высокий | Open |
| BUG-ADMIN-9 | [#11](https://github.com/darykuropteva/qa-ecommerce-backend/issues/11) | Неинформативное сообщение при передаче строки в поле categoryId | `POST /api/products` | 🟡 Высокий | Open |
| BUG-ADMIN-10 | [#12](https://github.com/darykuropteva/qa-ecommerce-backend/issues/12) | Отсутствует валидация типа данных поля totalStock | `POST /api/products` | 🟡 Высокий | Open |
| BUG-ADMIN-11 | [#13](https://github.com/darykuropteva/qa-ecommerce-backend/issues/13) | Неинформативное сообщение при description > 500 символов | `PUT /api/products/{id}` | 🟡 Высокий | Open |
| BUG-ADMIN-12 | [#14](https://github.com/darykuropteva/qa-ecommerce-backend/issues/14) | Не обнуляет поля которые не переданы в запросе | `PUT /api/products/{id}` | 🟡 Высокий | Open |
| BUG-ADMIN-13 | [#15](https://github.com/darykuropteva/qa-ecommerce-backend/issues/15) | Возвращает 400 без информативного сообщения при totalStock ниже reservedStock | `PUT /api/products/{id}` | 🟡 Высокий | Open |
| BUG-ADMIN-14 | [#16](https://github.com/darykuropteva/qa-ecommerce-backend/issues/16) | Возвращает 400 вместо 409 при наличии активной резервации | `DELETE /api/products/{id}` | 🟡 Высокий | Open |
| BUG-ADMIN-16 | [#17](https://github.com/darykuropteva/qa-ecommerce-backend/issues/17) | Возвращает 400 без информативного сообщения при отмене резервации CONFIRMED | `DELETE /api/stocks/reservations/{code}` | 🟡 Высокий | Open |
| BUG-ADMIN-17 | [#18](https://github.com/darykuropteva/qa-ecommerce-backend/issues/18) | Возвращает 400 без информативного сообщения при недостаточном stock | `POST /api/stocks/products/{productId}/reserve` | 🟡 Высокий | Open |
| BUG-ADMIN-18 | [#19](https://github.com/darykuropteva/qa-ecommerce-backend/issues/19) | Возвращает 400 вместо 403 при запросе с токеном User | `POST /api/stocks/products/{productId}/reserve` | 🟡 Высокий | Open |
| BUG-ADMIN-19 | [#20](https://github.com/darykuropteva/qa-ecommerce-backend/issues/20) | Возвращает 400 вместо 404 при несуществующем code | `POST /api/stocks/reservations/{code}/confirm` | 🟡 Высокий | Open |
| BUG-ADMIN-20 | [#21](https://github.com/darykuropteva/qa-ecommerce-backend/issues/21) | Возвращает 400 вместо 404 при несуществующем code | `DELETE /api/stocks/reservations/{code}` | 🟡 Высокий | Open |

---

## Группировка по сервисам / Grouped by Service

### product-service (http://localhost:8082)

| Эндпоинт | Багов | Issues |
|---|---|---|
| `POST /api/categories` | 1 | [#3](https://github.com/darykuropteva/qa-ecommerce-backend/issues/3) |
| `PUT /api/categories/{id}` | 1 | [#4](https://github.com/darykuropteva/qa-ecommerce-backend/issues/4) |
| `POST /api/products` | 8 | [#5](https://github.com/darykuropteva/qa-ecommerce-backend/issues/5) [#6](https://github.com/darykuropteva/qa-ecommerce-backend/issues/6) [#7](https://github.com/darykuropteva/qa-ecommerce-backend/issues/7) [#8](https://github.com/darykuropteva/qa-ecommerce-backend/issues/8) [#9](https://github.com/darykuropteva/qa-ecommerce-backend/issues/9) [#10](https://github.com/darykuropteva/qa-ecommerce-backend/issues/10) [#11](https://github.com/darykuropteva/qa-ecommerce-backend/issues/11) [#12](https://github.com/darykuropteva/qa-ecommerce-backend/issues/12) |
| `PUT /api/products/{id}` | 3 | [#13](https://github.com/darykuropteva/qa-ecommerce-backend/issues/13) [#14](https://github.com/darykuropteva/qa-ecommerce-backend/issues/14) [#15](https://github.com/darykuropteva/qa-ecommerce-backend/issues/15) |
| `DELETE /api/products/{id}` | 1 | [#16](https://github.com/darykuropteva/qa-ecommerce-backend/issues/16) |
| `POST /api/stocks/products/{productId}/reserve` | 3 | [#18](https://github.com/darykuropteva/qa-ecommerce-backend/issues/18) [#19](https://github.com/darykuropteva/qa-ecommerce-backend/issues/19) [#2](https://github.com/darykuropteva/qa-ecommerce-backend/issues/2) |
| `DELETE /api/stocks/reservations/{code}` | 3 | [#17](https://github.com/darykuropteva/qa-ecommerce-backend/issues/17) [#20](https://github.com/darykuropteva/qa-ecommerce-backend/issues/20) [#21](https://github.com/darykuropteva/qa-ecommerce-backend/issues/21) |
| `POST /api/stocks/reservations/{code}/confirm` | 1 | [#21](https://github.com/darykuropteva/qa-ecommerce-backend/issues/21) |

### order-service (http://localhost:8084)

| Эндпоинт | Багов | Issues |
|---|---|---|
| `PUT /api/admin/orders/{id}/status` | 1 | [#1](https://github.com/darykuropteva/qa-ecommerce-backend/issues/1) |
