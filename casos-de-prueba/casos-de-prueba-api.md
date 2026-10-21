# Casos de prueba de API — Urban Grocers (Sprint 4)

Casos de prueba negativos y de valores límite ejecutados con Postman sobre dos endpoints. Cada caso que falló generó un reporte de bug en Jira (ver [`reportes-de-bugs/`](../reportes-de-bugs)).

## Endpoint 1: `POST /api/v1/kits/:id/products`

| ID | Condición probada | Resultado esperado | Resultado obtenido | Estado | Bug |
|---|---|---|---|---|---|
| CP-API-01 | `:id` del kit no numérico (`abc`) | 400 o 404 con mensaje claro | 500 Internal Server Error | ❌ Falló | UGS4G-1 |
| CP-API-02 | ID de producto inexistente | Rechazar la solicitud | Agrega un registro corrupto (sin id, name, price, weight ni units) | ❌ Falló | UGS4G-2 |
| CP-API-03 | `id` de un producto como string | 400 Bad Request | 500 Internal Server Error | ❌ Falló | UGS4G-3 |
| CP-API-04 | `quantity` negativo (-1) | 400 Bad Request | Acepta y persiste el valor | ❌ Falló | UGS4G-4 |
| CP-API-05 | `productsList` como objeto en lugar de array | 400 Bad Request | 500 (`productsList.find is not a function`) | ❌ Falló | UGS4G-5 |

## Endpoint 2: `POST /order-and-go/v1/delivery`

### Validación de campos obligatorios y tipos

| ID | Condición probada | Resultado esperado | Resultado obtenido | Estado | Bug |
|---|---|---|---|---|---|
| CP-API-06 | Falta `productsCount` | 400 Bad Request | 200 OK | ❌ Falló | UGS4G-6 |
| CP-API-07 | Falta `productsWeight` | 400 Bad Request | 200 OK | ❌ Falló | UGS4G-7 |
| CP-API-08 | Falta `deliveryTime` | 400 Bad Request | 200 OK | ❌ Falló | UGS4G-8 |
| CP-API-09 | `productsCount` string no numérico | 400 Bad Request | 200 OK | ❌ Falló | UGS4G-9 |
| CP-API-10 | `productsWeight` string no numérico | 400 Bad Request | 200 OK | ❌ Falló | UGS4G-10 |
| CP-API-11 | `deliveryTime` string no numérico | 400 Bad Request | 200 OK | ❌ Falló | UGS4G-11 |
| CP-API-12 | Body como array en vez de objeto | 400 Bad Request | 200 OK | ❌ Falló | UGS4G-12 |
| CP-API-13 | Body completamente vacío | 400 Bad Request | 200 OK | ❌ Falló | UGS4G-13 |

### Reglas de negocio y valores límite

| ID | Condición probada | Resultado esperado | Resultado obtenido | Estado | Bug |
|---|---|---|---|---|---|
| CP-API-14 | `deliveryTime` antes de la apertura (08:00) | `isItPossibleToDeliver: false` | `true` | ❌ Falló | UGS4G-14 |
| CP-API-15 | `deliveryTime` después del cierre (22:00) | `isItPossibleToDeliver: false` | `true` | ❌ Falló | UGS4G-15 |
| CP-API-16 | `productsCount` por encima del máximo (15) | `isItPossibleToDeliver: false` | `true` | ❌ Falló | UGS4G-16 |
| CP-API-17 | `productsWeight` = 3.1 kg (límite inferior del 2.º tramo de precio) | Aplicar el tramo de precio correspondiente | No aplica correctamente el tramo | ❌ Falló | UGS4G-17 |
| CP-API-18 | `productsWeight` por encima del máximo (6 kg) | `isItPossibleToDeliver: false` | `true` | ❌ Falló | UGS4G-18 |
| CP-API-19 | `productsCount` negativo (-1) | No debe marcarse como disponible | `true` | ❌ Falló | UGS4G-19 |
| CP-API-20 | `productsWeight` negativo (-1) | No debe marcarse como disponible | `true` | ❌ Falló | UGS4G-20 |
