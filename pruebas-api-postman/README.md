# Pruebas de API con Postman

## Cómo subir tu colección real de Postman aquí

1. Abre Postman → clic derecho sobre tu colección → **Export**.
2. Elige el formato **Collection v2.1** → Export.
3. Se descarga un archivo `.json` a tu computador.
4. Sube ese archivo `.json` a esta carpeta en GitHub (lo explico en los pasos generales más abajo).

## Qué documentar por cada endpoint probado

| Endpoint | Método | Qué valida | Resultado |
|---|---|---|---|
| /api/ejemplo | GET | Devuelve status 200 y estructura correcta | ✅ Pasó |
| /api/ejemplo | POST | Rechaza campos vacíos con status 400 | ✅ Pasó |

## Ejemplo de script de prueba en Postman (pestaña "Tests")
```javascript
pm.test("El status code es 200", function () {
    pm.response.to.have.status(200);
});

pm.test("La respuesta incluye el campo esperado", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("id");
});
```

> 💡 Si tus pruebas en Postman ya usan `pm.test(...)` como en el ejemplo de arriba, **eso ya es automatización de pruebas de API** — puedes decirlo con confianza en tu CV y en entrevista.

---
*Reemplaza esta tabla y agrega tu colección `.json` real de un proyecto de TripleTen.*
