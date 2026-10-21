# BUG-01: El endpoint POST /api/v1/kits/:id/products devuelve 500 Internal Server Error en lugar de un error de validación cuando el parámetro `:id` no tiene formato numérico

**Clave en Jira:** UGS4G-1
**Proyecto:** Urban Grocers – Sprint 4 (API)
**Prioridad:** Alta
**Severidad:** Alta — un input de cliente no controlado provoca un error 5xx en el servidor, lo que indica ausencia de validación en la capa de entrada y riesgo para la estabilidad del sistema.
**Entorno:** API de Urban Grocers (probada con Postman)

## Pasos para reproducir
1. Enviar una solicitud `POST` a `{{baseUrl}}/api/v1/kits/abc/products`
2. Usar como body:

```json
{
  "productsList": [
    {
      "id": 1,
      "quantity": 1
    }
  ]
}
```

3. Revisar el código de estado y el cuerpo de la respuesta.

## Resultado esperado (RE)
- Código de estado: **400 Bad Request** (parámetro `:id` con formato inválido) o **404 Not Found**.
- Mensaje de error claro indicando que el ID del kit no es válido.
- No se agrega ningún producto.

## Resultado actual (RA)
- Código de estado: **500 Internal Server Error**.
- Cuerpo de la respuesta: página de error genérica del servidor, sin un mensaje de validación específico.
- El sistema no valida el formato del parámetro antes de procesarlo, lo que provoca una excepción no controlada en el backend.

## Evidencia
> 📎 Agrega aquí la captura de pantalla de Postman (puedes arrastrar la imagen directamente al editor de GitHub). En Jira está adjunta como `image-20260827-002738.png`.
