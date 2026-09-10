# API REST de Gestión de Productos

API REST desarrollada en **Python** con **Flask**, para el registro, consulta, actualización y eliminación de productos, con persistencia en una base de datos **MySQL/MariaDB**.

## 🛠️ Tecnologías utilizadas

- Python
- Flask + Flask-CORS
- MySQL / MariaDB (`mysql-connector-python`)
- Postman (pruebas y documentación de endpoints)

## 📁 Estructura del proyecto

```
rest-api-productos/
├── ConexionBasededatos.py   # Clase de conexión a la base de datos MySQL
├── Controladores.py         # Rutas de la API (Flask) y punto de entrada de la app
├── Modelproductos.py        # Acceso a datos: consultas SQL sobre la tabla `productos`
├── prueba.sql                # Script de creación e inserción de datos de la tabla `productos`
└── .gitignore
```

## ⚙️ Instalación y configuración

1. Clona el repositorio:
   ```bash
   git clone https://github.com/CarlosRojano05/rest-api-productos.git
   cd rest-api-productos
   ```

2. Instala las dependencias:
   ```bash
   pip install flask flask-cors mysql-connector-python
   ```

3. Crea la base de datos `prueba` importando el script `prueba.sql` en tu gestor de MySQL/MariaDB (phpMyAdmin, Workbench, consola, etc.). Esto crea la tabla `productos` con datos de ejemplo.

4. Verifica los datos de conexión en `ConexionBasededatos.py` (por defecto apunta a un MySQL local):
   ```python
   host = "localhost"
   port = "3306"
   user = "root"
   password = ""
   database = "prueba"
   ```

5. Ejecuta la API:
   ```bash
   python Controladores.py
   ```
   La API quedará disponible en `http://127.0.0.1:5000/` (modo debug activado).

## 🗄️ Modelo de datos

Tabla `productos`:

| Campo    | Tipo           | Detalle                     |
|----------|----------------|------------------------------|
| id       | INT(11)        | Llave primaria, autoincremental |
| nombre   | VARCHAR(100)   | Nombre del producto          |
| precio   | DECIMAL(10,2)  | Precio del producto          |

## 📌 Endpoints

| Método | Endpoint                        | Descripción                              |
|--------|----------------------------------|--------------------------------------------|
| GET    | `/productos`                    | Lista todos los productos                  |
| GET    | `/producto/<id>`                | Obtiene un producto por su ID              |
| POST   | `/nuevo_producto`                | Crea un nuevo producto                     |
| PUT    | `/actualizar_producto/<id>`      | Actualiza nombre y/o precio de un producto |
| DELETE | `/eliminar_producto/<id>`        | Elimina un producto por su ID (valida que exista) |

### Ejemplo: crear producto — `POST /nuevo_producto`

```json
{
  "nombre": "Mouse",
  "precio": 35.00
}
```

### Ejemplo: actualizar producto — `PUT /actualizar_producto/10`

```json
{
  "nombre": "Mouse inalámbrico",
  "precio": 45.00
}
```
> Se puede enviar solo `nombre` o solo `precio`; si no se envía ningún dato, la API responde `400`.

### Ejemplo: eliminar producto — `DELETE /eliminar_producto/10`

Si el producto no existe, la API responde `404` con `{"mensaje": "el producto no existe"}`.

## 🧪 Pruebas

Todos los endpoints fueron probados y documentados con **Postman**.
<!-- opcional: si exportas tu colección de Postman (.json) y la subes al repo, enlázala aquí -->

## 👤 Autor

**Carlos Manuel Rojano Camargo**
[GitHub](https://github.com/CarlosRojano05) · carlosrojanocamargo2@gmail.com
