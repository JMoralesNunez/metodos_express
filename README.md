# 📘 Métodos más usados en Express

En Express, el objeto que se crea con `express()` (normalmente llamado `app`) es una instancia de la aplicación, y sobre él puedes usar varios métodos para definir el comportamiento de tu API.

---

## 🔧 Métodos más comunes

### 1. `app.use()`
**Sirve para usar middlewares.**

Un *middleware* es una función que se ejecuta antes de que la solicitud llegue a las rutas.

```js
app.use(express.json()); // Middleware para leer JSON en el cuerpo de las peticiones
```

También se puede usar para montar rutas:

```js
const usersRouter = require('./routes/users');
app.use('/api/users', usersRouter);
```

---

### 2. `app.get(ruta, callback)`
**Define una ruta que responde a una solicitud GET.**

```js
app.get('/saludo', (req, res) => {
  res.send('¡Hola mundo!');
});
```

---

### 3. `app.post(ruta, callback)`
**Define una ruta que responde a una solicitud POST.**

Se usa para **crear datos** (como enviar formularios o guardar usuarios).

```js
app.post('/usuarios', (req, res) => {
  const nuevoUsuario = req.body;
  res.status(201).json(nuevoUsuario);
});
```

---

### 4. `app.put(ruta, callback)`
**Actualiza completamente un recurso existente.**

```js
app.put('/usuarios/:id', (req, res) => {
  const id = req.params.id;
  const datosActualizados = req.body;
  res.send(`Usuario con ID ${id} actualizado`);
});
```

---

### 5. `app.patch(ruta, callback)`
**Actualiza parcialmente un recurso.**

```js
app.patch('/usuarios/:id', (req, res) => {
  res.send('Datos parcialmente actualizados');
});
```

---

### 6. `app.delete(ruta, callback)`
**Elimina un recurso.**

```js
app.delete('/usuarios/:id', (req, res) => {
  res.send(`Usuario con ID ${req.params.id} eliminado`);
});
```

---

### 7. `app.listen(puerto, callback)`
**Inicia el servidor y lo pone a escuchar en un puerto.**

```js
app.listen(3000, () => {
  console.log('Servidor iniciado en http://localhost:3000');
});
```

---

## 🧠 Objetos importantes

- `req` → representa la solicitud del cliente. Puedes acceder a:
  - `req.body` (cuerpo de la petición)
  - `req.params` (parámetros de la URL)
  - `req.query` (parámetros del query string)
- `res` → representa la respuesta que se envía al cliente

---

## ✅ Resumen rápido

| Método         | ¿Para qué se usa?                         |
|----------------|-------------------------------------------|
| `app.use()`     | Middleware (autenticación, JSON, rutas)   |
| `app.get()`     | Obtener datos                            |
| `app.post()`    | Crear datos                              |
| `app.put()`     | Reemplazar datos                         |
| `app.patch()`   | Actualizar parcialmente datos            |
| `app.delete()`  | Eliminar datos                           |
| `app.listen()`  | Iniciar el servidor                      |

---
`
