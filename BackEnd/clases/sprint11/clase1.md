# Express.js

## Introducción

Express.js, o simplemente Express, es un marco de aplicación web de back-end para construir APIs RESTful con Node.js. Se lanzó como software libre y de código abierto bajo la licencia MIT. Está diseñado para construir aplicaciones web y APIs. Se le ha llamado el marco de servidor estándar de facto para Node.js.

## Características

### Enrutamiento Robusto

Express.js proporciona un potente sistema de enrutamiento que te permite definir diferentes rutas para manejar rutas URL específicas. Puedes crear endpoints para diferentes métodos HTTP (GET, POST, PUT, DELETE) y ejecutar código específico cuando se recibe una solicitud coincidente.

```javascript
const express = require("express");
const app = express();

// Manejo de solicitudes GET a la ruta raíz
app.get("/", (req, res) => {
  res.send("¡Hola, Mundo!");
});

// Manejo de solicitudes POST a la ruta raíz
app.post("/", (req, res) => {
  res.send("¡Una solicitud POST recibida!");
});

// Escucha en el puerto 3000
app.listen(3000, () => {
  console.log("Aplicación escuchando en el puerto 3000");
});
```

### HTTP Helpers de Alto Rendimiento

Proporciona una serie de métodos de respuesta en el objeto de respuesta (res), como res.download(), res.end(), res.json(), res.send(), y res.status(). Estos helpers facilitan el manejo de las respuestas HTTP.

```javascript
app.get('/', (req, res) => {
// Enviar una respuesta JSON
res.json({ mensaje: '¡Hola, Mundo!' });
});

app.get('/descargar', (req, res) => {
// Iniciar una descarga de archivo
var file = \_\_dirname + '/descargar.txt';
res.download(file);
});
```

### Programación Asíncrona

Es compatible con la programación asíncrona, permitiendo escribir código no bloqueante que puede manejar múltiples solicitudes simultáneamente. Esto es especialmente útil cuando estás realizando operaciones que consumen mucho tiempo, como leer archivos o consultar una base de datos.

```javascript
app.get("/usuarios", async (req, res) => {
  try {
    // Supongamos que getUserList es una función que obtiene una lista de usuarios de una base de datos
    const usuarios = await getUserList();
    res.json(usuarios);
  } catch (error) {
    res.status(500).send(error);
  }
});
```

## Ejemplo de código

El siguiente programa responderá a las solicitudes HTTP GET con el texto '¡Hola, tu solicitud ha sido recibida!', y escuchará el puerto en el que se está ejecutando el programa; Puerto 2000, en este caso.

```javascript
// Importar la biblioteca Express.
const express = require("express");

// Inicializando la aplicación.
const app = express();

// Obteniendo la solicitud de ruta y enviando la respuesta con texto
app.get("/", (req, res) => {
  res.send("¡Hola, tu solicitud ha sido recibida!");
});

// Escuchar en el puerto 2000
app.listen(2000, () => {
  console.log("escuchando en http://localhost:2000");
});
```
