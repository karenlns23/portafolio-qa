# Pruebas de API con Postman

Pruebas funcionales sobre dos endpoints de la API de Urban Grocers (Sprint 4), enfocadas en validación de entradas y reglas de negocio.

## Endpoints probados

| Endpoint | Método | Qué se validó | Bugs |
|---|---|---|---|
| `/api/v1/kits/:id/products` | POST | Formato del parámetro `:id`, productos inexistentes, tipo de dato del `id` de producto, cantidades negativas y estructura de `productsList` | UGS4G-1 a UGS4G-5 |
| `/order-and-go/v1/delivery` | POST | Campos obligatorios, tipos de dato, body vacío o con formato incorrecto, horario de atención, límites de artículos y peso, tramos de precio y valores negativos | UGS4G-6 a UGS4G-20 |

## Tipos de prueba aplicados
- **Pruebas negativas:** campos faltantes, valores no numéricos, body vacío, body con formato incorrecto.
- **Valores límite:** apertura (08:00) y cierre (22:00), máximo de 15 artículos, máximo de 6 kg, límite inferior del segundo tramo de precio (3.1 kg).
- **Validación de códigos de estado:** se verificó que las entradas inválidas devuelvan `400 Bad Request` y no `500 Internal Server Error` ni `200 OK`.

## Documentación relacionada
- [Casos de prueba de API](../casos-de-prueba/casos-de-prueba-api.md)
- [Reportes de bugs](../reportes-de-bugs)
- [Plan de pruebas](../plan-de-pruebas/plan-de-pruebas-api-urban-grocers.md)
