# Reportes de bugs

Todos los bugs fueron documentados en **Jira** con pasos para reproducir, resultado esperado (RE), resultado actual (RA), entorno, prioridad y severidad, más evidencia en captura de pantalla.

📄 Ejemplo completo: [BUG-01 — Error 500 con `:id` no numérico](./BUG-01-kits-id-no-numerico.md)

---

## Proyecto `UGS4G` — Urban Grocers (API) · 20 bugs

| Clave | Endpoint | Resumen |
|---|---|---|
| UGS4G-1 | POST `/api/v1/kits/:id/products` | Devuelve 500 en lugar de un error de validación cuando `:id` no es numérico |
| UGS4G-2 | POST `/api/v1/kits/:id/products` | Agrega un registro corrupto al enviar un ID de producto inexistente |
| UGS4G-3 | POST `/api/v1/kits/:id/products` | Devuelve 500 en lugar de 400 cuando el `id` de un producto es string |
| UGS4G-4 | POST `/api/v1/kits/:id/products` | Acepta y persiste `quantity` negativo (-1) |
| UGS4G-5 | POST `/api/v1/kits/:id/products` | Devuelve 500 en lugar de 400 cuando `productsList` es un objeto y no un array |
| UGS4G-6 | POST `/order-and-go/v1/delivery` | 200 OK en lugar de 400 cuando falta `productsCount` |
| UGS4G-7 | POST `/order-and-go/v1/delivery` | 200 OK en lugar de 400 cuando falta `productsWeight` |
| UGS4G-8 | POST `/order-and-go/v1/delivery` | 200 OK en lugar de 400 cuando falta `deliveryTime` |
| UGS4G-9 | POST `/order-and-go/v1/delivery` | 200 OK en lugar de 400 cuando `productsCount` es string no numérico |
| UGS4G-10 | POST `/order-and-go/v1/delivery` | 200 OK en lugar de 400 cuando `productsWeight` es string no numérico |
| UGS4G-11 | POST `/order-and-go/v1/delivery` | 200 OK en lugar de 400 cuando `deliveryTime` es string no numérico |
| UGS4G-12 | POST `/order-and-go/v1/delivery` | 200 OK en lugar de 400 cuando el body es un array |
| UGS4G-13 | POST `/order-and-go/v1/delivery` | 200 OK en lugar de 400 cuando el body está vacío |
| UGS4G-14 | POST `/order-and-go/v1/delivery` | Marca la entrega como disponible antes de la apertura (08:00) |
| UGS4G-15 | POST `/order-and-go/v1/delivery` | Marca la entrega como disponible después del cierre (22:00) |
| UGS4G-16 | POST `/order-and-go/v1/delivery` | Marca la entrega como disponible cuando `productsCount` supera el máximo (15) |
| UGS4G-17 | POST `/order-and-go/v1/delivery` | No aplica correctamente el tramo de precios en el límite inferior del segundo tramo (3.1 kg) |
| UGS4G-18 | POST `/order-and-go/v1/delivery` | Marca la entrega como disponible cuando `productsWeight` supera el máximo (6 kg) |
| UGS4G-19 | POST `/order-and-go/v1/delivery` | Marca la entrega como disponible con `productsCount` negativo (-1) |
| UGS4G-20 | POST `/order-and-go/v1/delivery` | Marca la entrega como disponible con `productsWeight` negativo (-1) |

## Proyecto `S3KLNSG` — App de reserva de autos · 28 bugs

**Mapa y reserva**

| Clave | Resumen |
|---|---|
| S3KLNSG-1 | El mapa no muestra vehículos de todas las tarifas disponibles, sin importar cuál esté seleccionada |
| S3KLNSG-2 | El usuario no puede elegir un automóvil en el mapa y reservarlo haciendo clic sobre su ícono |
| S3KLNSG-3 | El auto más cercano no se muestra con un ícono más grande y un recuadro negro con la marca |
| S3KLNSG-4 | Falta el ícono de persona caminando junto al texto de minutos y el tiempo de espera gratuito |
| S3KLNSG-9 | No aparece el recuadro negro con la marca sobre el ícono del automóvil reservado |
| S3KLNSG-10 | La ventana no muestra, en negrita, la marca y la placa del vehículo |
| S3KLNSG-11 | La ventana de confirmación no aparece centrada sobre el mapa |

**Pago con tarjeta (validación de campos)**

| Clave | Resumen |
|---|---|
| S3KLNSG-12 | Es posible reservar un automóvil sin ninguna tarjeta agregada |
| S3KLNSG-13 | Con los 12 dígitos completos, el botón "Agregar tarjeta" no se activa |
| S3KLNSG-14 | Comportamiento incorrecto al intentar introducir un 13.º dígito en "Número de tarjeta" |
| S3KLNSG-15 | "Número de tarjeta" acepta letras |
| S3KLNSG-16 | "Número de tarjeta" acepta caracteres especiales |
| S3KLNSG-17 | "Número de tarjeta" acepta decimales o fracciones |
| S3KLNSG-18 | "Número de tarjeta" acepta signos + o - |
| S3KLNSG-19 | "Número de tarjeta" acepta un espacio introducido manualmente |
| S3KLNSG-20 | No se agregan automáticamente los espacios con formato nnnn nnnn nnnn al perder el foco |
| S3KLNSG-21 | "Código" acepta un 3.er carácter numérico |
| S3KLNSG-22 | "Código" acepta el valor "00" |
| S3KLNSG-23 | "Código" acepta letras |
| S3KLNSG-24 | "Código" acepta caracteres especiales |
| S3KLNSG-25 | "Código" acepta decimales o fracciones |
| S3KLNSG-26 | "Código" acepta signos + o - |
| S3KLNSG-27 | Al agregar una tarjeta válida, no se muestran los últimos 4 dígitos en "Método de pago" |

**Flujos de reserva**

| Clave | Resumen |
|---|---|
| S3KLNSG-28 | El botón "Reservar" no responde cuando falta la licencia de conducir |
| S3KLNSG-29 | Al reservar sin método de pago se omite la solicitud de tarjeta |
| S3KLNSG-30 | Al borrar "Desde" y "Hasta" se pierde la configuración previa y no se puede continuar |
| S3KLNSG-31 | El botón "Cancelar" no responde durante el tiempo de espera gratuito |
| S3KLNSG-32 | El temporizador no cambia a tiempo de uso compartido al agotarse la espera gratuita |

## Proyecto `S6KLNSG` — App de pedidos con mapa de restaurantes · 7 bugs

| Clave | Resumen |
|---|---|
| S6KLNSG-1 | No se muestra el tiempo estimado de entrega en el punto de recogida |
| S6KLNSG-2 | El precio de "Hamburguesa vegana de remolacha" es 15 $ en lugar de 25 $ |
| S6KLNSG-3 | El importe total no incluye el costo de la entrega |
| S6KLNSG-4 | El mapa no muestra el costo de los platillos pedidos en cada restaurante |
| S6KLNSG-5 | El mapa no muestra el tiempo de preparación restante de cada restaurante |
| S6KLNSG-6 | El mapa no muestra el tiempo de entrega desde cada restaurante hasta el punto de recogida |
| S6KLNSG-7 | La app se cierra sin mostrar mensaje de error al denegar el permiso de geolocalización |
