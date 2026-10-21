# Plan de pruebas: API de Urban Grocers (Sprint 4)

## Objetivo
Verificar que los endpoints de kits y de entrega validen correctamente las entradas inválidas y respeten las reglas de negocio de horario, cantidad, peso y precio.

## Alcance
**Incluye:**
- `POST /api/v1/kits/:id/products`
- `POST /order-and-go/v1/delivery`

**Tipos de prueba:** negativas (campos faltantes, tipos incorrectos, body vacío o con formato incorrecto) y de valores límite (horario, cantidad máxima, peso máximo, tramos de precio, valores negativos).

## Estrategia
- Ejecución de solicitudes en **Postman** y revisión del código de estado y del cuerpo de la respuesta.
- Registro de cada defecto en **Jira** con pasos para reproducir, resultado esperado, resultado actual, entorno, prioridad y severidad.

## Criterios de aceptación
- Toda entrada inválida debe responder `400 Bad Request` con un mensaje claro, sin errores `500` ni respuestas `200 OK`.
- La entrega no debe marcarse como disponible fuera del horario de atención ni al superar los límites de cantidad o peso.
- No deben persistirse datos corruptos ni valores negativos.

## Resultados
Se reportaron **20 defectos** (UGS4G-1 a UGS4G-20):

| Categoría | Cantidad | Claves |
|---|---|---|
| Errores 500 por entradas sin validar (`kits`) | 3 | UGS4G-1, 3, 5 |
| Datos inválidos o corruptos aceptados (`kits`) | 2 | UGS4G-2, 4 |
| Validación de entrada ausente (`delivery`) | 8 | UGS4G-6 a 13 |
| Reglas de negocio incumplidas (`delivery`) | 7 | UGS4G-14 a 20 |

## Documentación relacionada
- [Casos de prueba de API](../casos-de-prueba/casos-de-prueba-api.md)
- [Reportes de bugs](../reportes-de-bugs)
