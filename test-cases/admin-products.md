# Тест-кейсы: Управление товарами и складом

## Описание

Тестирование функциональности управления товарами и складскими остатками.

## Покрываемые эндпоинты

* POST /api/products
* PUT /api/products/{id}
* DELETE /api/products/{id}
* POST /api/stocks/products/{productId}/reserve
* DELETE /api/stocks/reservations/{code}

## Статистика

| Показатель        | Значение                   |
| ----------------- | -------------------------- |
| Всего тест-кейсов | 65                         |
| Найдено дефектов  | BUG-ADMIN-3 — BUG-ADMIN-20 |
| Статус            | Выполнено                  |

## Полные тест-кейсы

Подробное описание тест-кейсов доступно в файле:

[admin-test-case.xlsx](https://github.com/darykuropteva/qa-ecommerce-backend/blob/main/test-cases/admin-test-case.xlsx)

## Покрытие

* CRUD операции с товарами
* Валидация данных товара
* Работа со складом
* Резервирование товара
* Отмена резервации
* Проверка бизнес-логики склада
* Проверка HTTP-статусов
