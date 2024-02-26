# Swagger y Swagger UI

## Descripción

Swagger es una herramienta de código abierto utilizada para diseñar, construir y documentar servicios web RESTful. Proporciona soporte para la especificación de OpenAPI, un estándar de la industria para describir APIs RESTful. Swagger UI es una herramienta complementaria que genera una interfaz de usuario interactiva a partir de la descripción de tu API, permitiendo a los desarrolladores explorar y probar la API directamente desde su navegador.

## Uso de Swagger y Swagger UI

### Configuración de Swagger

Configura Swagger para que pueda leer la descripción de tu API. Crea un objeto de opciones con información como la definición de la API y la ubicación de los archivos que contienen la descripción de la API.

```javascript
const swaggerJSDoc = require("swagger-jsdoc");

const swaggerDefinition = {
  info: {
    title: "Mi API",
    version: "1.0.0",
    description: "Descripción de mi API",
  },
  host: "localhost:3000",
  basePath: "/",
};

const options = {
  swaggerDefinition,
  apis: ["./routes/*.js"], // Ruta a los archivos que contienen la documentación de la API
};

const swaggerSpec = swaggerJSDoc(options);
```

### Documentación de la API

Utiliza comentarios en el código para documentar la API. Estos comentarios deben seguir un formato específico para que Swagger pueda leerlos. Ejemplo:

```javascript
/**
 * @swagger
 * /users:
 *   get:
 *     tags:
 *       - Users
 *     description: Returns all users
 *     produces:
 *       - application/json
 *     responses:
 *       200:
 *         description: An array of users
 */
router.get("/users", (req, res) => {
  // ...
});
```

### Generación de la documentación

Una vez documentada la API, genera la documentación con Swagger utilizando la función `swaggerJSDoc` con el objeto de opciones creado anteriormente.

### Servir Swagger UI

Finalmente, sirve Swagger UI en tu aplicación utilizando el middleware `swagger-ui-express` y la documentación generada por Swagger. Por defecto, Swagger UI se sirve en la ruta `/api-docs`.

```javascript
const swaggerUi = require("swagger-ui-express");

app.use("/api-docs", swaggerUi.serve, swaggerUi.setup(swaggerSpec));
```
