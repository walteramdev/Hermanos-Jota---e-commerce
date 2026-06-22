# Mueblería Hermanos Jota

Proyecto full-stack de e-commerce completo para una mueblería. La solución consta de un backend seguro en Express con MongoDB que gestiona autenticación, catálogo de productos y pedidos, junto con un frontend en React + Vite que ofrece navegación multipágina, sistema de autenticación JWT, gestión de estado global con Context API, carrito de compras funcional y proceso completo de checkout.

## Integrantes actuales del equipo

- Walter Arias Molino
- Tomás Sebastián Picco
- Federico Leonardis Ayala

#### Devs que pasaron por aquí: 
- Malena Zoe Blanco Di Beco


## � Enlaces de Producción

- **Frontend (Netlify)**: https://hermanos-jota-muebleria.netlify.app/
- **Backend (Render)**: https://hermanosjota-e-commerce.onrender.com

## �🎓 Credenciales de Prueba (Evaluadores)

Para evaluar las funcionalidades de **administrador**, utilice estas credenciales:

```
Email: admin@gmail.com
Contraseña: admin
```

**Acceso incluido:**
- ✅ Crear productos desde el catálogo (tarjeta con +)
- ✅ Editar productos existentes
- ✅ Eliminar productos con confirmación
- ✅ Todas las funcionalidades administrativas

----

## Características principales

### Frontend
- **Sistema de autenticación completo** con registro, login y persistencia de sesión
- **Rutas protegidas** con componente `ProtectedRoute` para páginas privadas
- **Gestión de estado global** con React Context API (autenticación y carrito)
- **Navegación multipágina** con React Router (home, catálogo, detalle, contacto, perfil, carrito)
- **UI condicional** que cambia según el estado de autenticación del usuario
- **Carrito de compras persistente** con localStorage por usuario (cada usuario mantiene su propio carrito)
- **Proceso de checkout protegido** que requiere autenticación
- **Página de perfil de usuario** con datos protegidos
- **Listado completo del catálogo** con búsqueda en tiempo real por nombre
- **Páginas de detalle dinámicas** que obtienen productos individuales desde la API
- **Sistema de administración completo** para crear, editar y eliminar productos (solo admins)
- **Tarjeta de agregar producto** en el catálogo para acceso rápido al formulario de creación (solo visible para admins)
- **Formulario de creación de productos** con features opcionales y dinámicas
- **Formulario de edición de productos** con pre-carga de datos existentes
- **Recarga automática del catálogo** después de crear, editar o eliminar productos
- **Modal de confirmación** para acciones destructivas (eliminar productos)
- **Responsive design** con CSS modular organizado por secciones
- **Optimistic updates** para mejorar la experiencia de usuario

### Backend
- **Autenticación segura con JWT** y hashing de contraseñas con bcrypt
- **Middleware de protección** para rutas que requieren autenticación
- **Middleware de autorización** para rutas de administrador
- **API RESTful** con Express y MongoDB/Mongoose
- **CRUD completo** de productos, usuarios y pedidos
- **Gestión de pedidos** asociados a usuarios autenticados
- **Modelo de datos flexible** con features opcionales (medidas, materiales, acabado, etc.)
- **Middleware de logging** personalizado para tracking de requests
- **CORS configurado** para desarrollo local y producción
- **Manejo centralizado de errores** con respuestas HTTP apropiadas
- **Variables de entorno** para configuración segura

## Tecnologías

### Frontend
- **React 19** - Librería de UI con hooks modernos
- **React Router 7** - Navegación y rutas dinámicas protegidas
- **React Context API** - Gestión de estado global (Auth y Carrito)
- **Vite** - Build tool y dev server de alta velocidad
- **CSS Modular** - Estilos organizados por componentes y páginas
- **Fetch API** - Comunicación con el backend
- **LocalStorage** - Persistencia de sesión y carrito

### Backend
- **Node.js 18+** - Runtime de JavaScript
- **Express 5** - Framework web minimalista
- **MongoDB Atlas** - Base de datos NoSQL en la nube
- **Mongoose** - ODM para MongoDB
- **JWT (jsonwebtoken)** - Autenticación basada en tokens
- **bcrypt** - Hashing seguro de contraseñas
- **dotenv** - Gestión de variables de entorno
- **nodemon** - Recarga automática en desarrollo
- **CORS** - Middleware para cross-origin requests

## Estructura de carpetas

```
hermanosJota_e-commerce/
├── backend/
│   ├── src/
│   │   ├── middleware/
│   │   │   └── logger.js           # Logging de requests HTTP
│   │   ├── models/
│   │   │   └── Product.js          # Modelo Mongoose de productos
│   │   └── routes/
│   │       └── productosRoutes.js  # Rutas de la API de productos
│   ├── data/
│   │   └── productos.js            # Datos de ejemplo (legacy)
│   ├── images/
│   │   └── productos/              # Imágenes de productos
│   ├── .env                        # Variables de entorno (no versionado)
│   ├── .env.example                # Plantilla de variables de entorno
│   ├── server.js                   # Punto de entrada del servidor
│   └── package.json
│
├── client/
│   ├── src/
│   │   ├── components/
│   │   │   ├── AddProductCard.jsx  # Tarjeta para agregar productos (admins)
│   │   │   ├── FeaturedProduct.jsx # Productos destacados en home
│   │   │   ├── Footer.jsx          # Footer del sitio
│   │   │   ├── Header.jsx          # Header con navegación y carrito
│   │   │   ├── ProductCard.jsx     # Tarjeta de producto en catálogo
│   │   │   ├── ProductDetail.jsx   # Vista detallada de producto
│   │   │   ├── ProtectedRoute.jsx  # HOC para rutas protegidas
│   │   │   └── ProductosPage.jsx   # Página de catálogo
│   │   ├── pages/
│   │   │   ├── CartPage.jsx        # Página del carrito de compras
│   │   │   ├── Catalogo.jsx        # Página del catálogo
│   │   │   ├── Contacto.jsx        # Formulario de contacto
│   │   │   ├── FormProductoEdit.jsx # Formulario de edición de productos
│   │   │   ├── FormProductoNuevo.jsx # Formulario de creación de productos
│   │   │   ├── HomePage.jsx        # Página de inicio
│   │   │   ├── LoginPage.jsx       # Página de inicio de sesión
│   │   │   ├── RegisterPage.jsx    # Página de registro
│   │   │   └── UserProfile.jsx     # Página de perfil de usuario
│   │   ├── context/
│   │   │   ├── CartContext.js      # Contexto del carrito
│   │   │   └── CartProvider.jsx    # Provider del carrito con persistencia por usuario
│   │   ├── auth/
│   │   │   ├── AuthContext.js      # Contexto de autenticación
│   │   │   └── AuthProvider.jsx    # Provider de autenticación con JWT
│   │   ├── hooks/
│   │   │   └── useProductos.js     # Hook personalizado (legacy)
│   │   ├── config/
│   │   │   └── api.js              # Configuración de URLs de API
│   │   ├── css/
│   │   │   ├── variables.css       # Variables CSS globales
│   │   │   ├── reset.css           # Reset de estilos
│   │   │   ├── global.css          # Estilos globales
│   │   │   ├── header.css          # Estilos del header
│   │   │   ├── footer.css          # Estilos del footer
│   │   │   ├── index.css           # Estilos de home
│   │   │   ├── productos.css       # Estilos del catálogo
│   │   │   ├── producto.css        # Estilos de detalle
│   │   │   ├── contacto.css        # Estilos de contacto
│   │   │   └── nuevo-producto.css  # Estilos del formulario admin
│   │   ├── App.jsx                 # Componente principal con rutas
│   │   └── main.jsx                # Punto de entrada React
│   ├── public/
│   │   └── assets/
│   │       └── img/                # Imágenes estáticas (logos, banners)
│   ├── .env.production             # Variables de entorno de producción
│   ├── netlify.toml                # Configuración de Netlify
│   ├── vite.config.js              # Configuración de Vite
│   └── package.json
│
├── .gitignore
├── package.json                     # Scripts raíz del proyecto
└── README.md                        # Este archivo
```

## Requisitos previos

- [Node.js](https://nodejs.org/) v18 o superior
- npm 9+ (incluido con Node)
- Cuenta de [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) (o MongoDB local)

## Instalación y configuración

### 1. Clonar el repositorio

```bash
git clone https://github.com/FedeLeonardis/hermanosJota_e-commerce.git
cd hermanosJota_e-commerce
```

### 2. Configurar el Backend

```bash
cd backend
npm install
```

Crear archivo `.env` basado en `.env.example`:

```bash
cp .env.example .env
```

Editar `.env` con tus credenciales:

```env
# Puerto del servidor
PORT=5000

# URI de MongoDB Atlas (o local: mongodb://localhost:27017/muebleria)
DB_URI=mongodb+srv://usuario:password@cluster.mongodb.net/muebleria

# Clave secreta para JWT (usa una clave fuerte y única)
JWT_SECRET=tu_clave_super_secreta_y_segura_12345

# URL del frontend (para CORS)
FRONTEND_URL=http://localhost:5173

# Entorno
NODE_ENV=development
```

**Importante:** 
- El `JWT_SECRET` debe ser una cadena larga y aleatoria para mayor seguridad.
- En producción, NUNCA expongas estas credenciales en el código.
- Usa variables de entorno en tu plataforma de hosting (Render, etc.).

### 3. Configurar el Frontend

```bash
cd ../client
npm install
```

Crear archivo `.env.local` para desarrollo:

```bash
echo "VITE_API_URL=http://localhost:5000" > .env.local
```

Para producción, editar `.env.production`:

```env
VITE_API_URL=https://tu-backend.onrender.com
```

## Ejecución en desarrollo

Cada subproyecto debe ejecutarse en terminales separadas.

### Backend

```bash
cd backend
npm run dev
```

El servidor escucha en `http://localhost:5000` (o el puerto definido en `.env`)

### Frontend

```bash
cd client
npm run dev
```

La aplicación se abre en `http://localhost:5173`

## Cuenta de demostración

Usuario de prueba para evaluación académica y demostración de funcionalidades administrativas.

```
Email: admin@gmail.com
Contraseña: admin
```

Con esta cuenta tendrá acceso a:
- ✅ Tarjeta de "Crear Producto" en el catálogo
- ✅ Botones de "Editar" y "Eliminar" en la vista de detalle de productos
- ✅ Todas las funcionalidades administrativas del sistema

**Nota:** Para probar como usuario regular, puede registrarse normalmente desde `/registro`.

## API Endpoints

El backend expone los siguientes endpoints:

### Autenticación y Usuarios

| Método | Ruta                      | Protección | Descripción                              |
|--------|---------------------------|------------|------------------------------------------|
| POST   | `/api/users/register`     | Pública    | Registra un nuevo usuario                |
| POST   | `/api/users/login`        | Pública    | Inicia sesión y devuelve JWT             |
| GET    | `/api/users/profile`      | 🔒 JWT     | Obtiene el perfil del usuario autenticado|
| GET    | `/api/users/check-session`| 🔒 JWT     | Verifica si la sesión es válida          |

### Productos

| Método | Ruta                  | Protección | Descripción                              |
|--------|-----------------------|------------|------------------------------------------|
| GET    | `/api/productos`      | Pública    | Obtiene todos los productos              |
| GET    | `/api/productos/:id`  | Pública    | Obtiene un producto por ID               |
| POST   | `/api/productos`      | 🔒 JWT     | Crea un nuevo producto                   |
| PUT    | `/api/productos/:id`  | 🔒 JWT     | Actualiza un producto existente          |
| DELETE | `/api/productos/:id`  | 🔒 JWT     | Elimina un producto                      |

### Pedidos

| Método | Ruta           | Protección | Descripción                              |
|--------|----------------|------------|------------------------------------------|
| POST   | `/api/orders`  | 🔒 JWT     | Crea un nuevo pedido (checkout)          |

**Nota:** Los endpoints marcados con 🔒 requieren enviar el JWT en el header:
```
Authorization: Bearer <token>
```

### Ejemplos de Request/Response

#### POST `/api/users/register` - Registrar usuario

**Request:**
```json
{
  "username": "juanperez",
  "email": "juan@example.com",
  "password": "miPassword123"
}
```

**Response (201):**
```json
{
  "_id": "674567890abcdef123456789",
  "username": "juanperez",
  "email": "juan@example.com",
  "roles": ["user"]
}
```

#### POST `/api/users/login` - Iniciar sesión

**Request:**
```json
{
  "email": "juan@example.com",
  "password": "miPassword123"
}
```

**Response (200):**
```json
{
  "message": "Login Exitoso",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "usuario": {
    "id": "674567890abcdef123456789",
    "username": "juanperez",
    "email": "juan@example.com",
    "roles": ["user"]
  }
}
```

#### GET `/api/productos/:id` - Obtener producto

**Response:**

```json
{
  "_id": "674567890abcdef123456789",
  "nombre": "Sofá Moderno",
  "descripcion": "Sofá de 3 plazas con diseño contemporáneo",
  "precio": 45000,
  "stock": 5,
  "imagenUrl": "https://example.com/sofa.jpg",
  "features": {
    "medidas": "200cm x 90cm x 85cm",
    "materiales": "Tela premium, estructura de madera",
    "tapizado": "Tapizado removible y lavable",
    "garantia": "2 años"
  }
}
```

#### POST `/api/productos` - Crear producto (Protegido)

**Headers:**
```
Authorization: Bearer <token>
```

**Request:**
```json
{
  "nombre": "Mesa de Comedor",
  "descripcion": "Mesa extensible para 6-8 personas",
  "precio": 35000,
  "stock": 3,
  "imagenUrl": "https://example.com/mesa.jpg",
  "features": {
    "medidas": "160cm x 90cm (extensible a 240cm)",
    "materiales": "Madera maciza de roble",
    "acabado": "Barniz mate",
    "extension": "Sistema de extensión central"
  }
}
```

#### POST `/api/orders` - Crear pedido (Protegido)

**Headers:**
```
Authorization: Bearer <token>
```

**Request:**
```json
{
  "items": [
    {
      "productoId": "674567890abcdef123456789",
      "cantidad": 2,
      "precioUnitario": 45000
    }
  ],
  "total": 90000
}
```

**Response (201):**
```json
{
  "message": "Pedido creado exitosamente",
  "order": {
    "_id": "674567890abcdef987654321",
    "usuario": "674567890abcdef123456789",
    "items": [...],
    "total": 90000,
    "createdAt": "2025-12-05T10:30:00.000Z"
  }
}
```

## Funcionalidades de Administrador

El sistema incluye un panel de administración completo para gestionar productos:

### Acceso Administrativo

Los usuarios con rol `admin` tienen acceso a funcionalidades especiales:

1. **Crear Productos**
   - Tarjeta especial con ícono `+` en el catálogo (solo visible para admins)
   - Formulario completo con validación
   - Features opcionales y dinámicas
   - Ruta: `/nuevo-producto` (protegida)

2. **Editar Productos**
   - Botón "Editar Producto" en la vista de detalle
   - Formulario pre-cargado con datos existentes
   - Actualización con confirmación
   - Ruta: `/productos/:id/editar` (protegida)

3. **Eliminar Productos**
   - Botón "Eliminar Producto" en la vista de detalle
   - Modal de confirmación antes de eliminar
   - Eliminación de la base de datos
   - Recarga automática del catálogo

### Carrito Persistente por Usuario

El sistema mantiene un carrito independiente para cada usuario:

- **Usuarios autenticados**: Carrito guardado en localStorage con clave única (`cart_user_{id}`)
- **Al cerrar sesión**: El carrito se guarda y limpia la vista
- **Al volver a iniciar sesión**: El carrito se restaura automáticamente
- **Usuarios diferentes**: Cada usuario ve solo su propio carrito

### Rutas Protegidas

Las siguientes rutas requieren autenticación:

- `/nuevo-producto` - Crear producto (admin)
- `/productos/:id/editar` - Editar producto (admin)
- `/perfil` - Perfil de usuario
- `/carrito` - Carrito de compras (checkout)

Si intentas acceder sin autenticación, serás redirigido a `/iniciar-sesion`.

## Modelos de Datos

### User Schema

```javascript
{
  username: String (required, unique),
  email: String (required, unique),
  password: String (required, hashed with bcrypt),
  roles: [String] (default: ["user"]),
  createdAt: Date (auto)
}
```

### Product Schema

```javascript
{
  nombre: String (required),
  descripcion: String (required),
  precio: Number (required, min: 0),
  stock: Number (required, min: 0),
  imagenUrl: String (required),
  features: {
    medidas: String,
    materiales: String,
    acabado: String,
    peso: String,
    capacidad: String,
    modulares: String,
    tapizado: String,
    confort: String,
    rotacion: String,
    garantia: String,
    almacenamiento: String,
    colchon: String,
    sostenibilidad: String,
    extension: String,
    apilables: String,
    incluye: String,
    cables: String,
    certificación: String,
    regulación: String,
    caracteristica: String
  }
}
```

Todos los campos de `features` son opcionales y pueden agregarse dinámicamente desde el formulario de administración.

### Order Schema

```javascript
{
  usuario: ObjectId (ref: 'User', required),
  items: [{
    producto: ObjectId (ref: 'Product', required),
    cantidad: Number (required, min: 1),
    precioUnitario: Number (required, min: 0)
  }],
  total: Number (required, min: 0),
  createdAt: Date (auto)
}
```

## Funcionalidades principales

### Autenticación y Autorización
- **Registro de usuarios** con validación y hashing seguro de contraseñas
- **Inicio de sesión** con generación de JWT
- **Persistencia de sesión** mediante localStorage
- **Rutas protegidas** en frontend y backend
- **Middleware de autenticación** que verifica JWT en cada request protegido
- **UI condicional** según estado de autenticación (muestra PERFIL/LOGOUT cuando está logueado)
- **Página de perfil** con datos del usuario autenticado

### Carrito de compras y pedidos
- **Gestión global del carrito** con Context API
- **Persistencia del carrito** en localStorage
- **Contador visual** en el header
- **Agregado de productos** con cantidad variable
- **Proceso de checkout protegido** que requiere autenticación
- **Creación de pedidos** asociados al usuario autenticado
- **Limpieza automática** del carrito tras pedido exitoso
- **Validación en backend** antes de crear pedidos

### Catálogo de productos
- Visualización en grid responsivo
- Búsqueda en tiempo real por nombre
- Navegación a detalle de cada producto

### Detalle de producto
- Carga dinámica desde API usando React Router params
- Visualización de features del producto
- Opción de agregar al carrito
- Botón de eliminación (solo admin) con modal de confirmación
- Manejo de estados de carga y error

### Administración
- Formulario de creación de productos
- Selector dinámico de features opcionales
- Validación de campos requeridos
- Navegación automática al producto creado
- Refetch automático de la lista de productos

## Scripts disponibles

### Backend (`/backend`)

```bash
npm run dev      # Desarrollo con nodemon (recarga automática)
npm start        # Producción con Node estándar
```

### Frontend (`/client`)

```bash
npm run dev      # Servidor de desarrollo con HMR
npm run build    # Build de producción en /dist
npm run preview  # Preview del build de producción
npm start        # Alias de preview --host (para red local)
```

## Deployment

### Backend (Render)

1. Crear nuevo Web Service en Render
2. Conectar repositorio de GitHub
3. Configurar build command: `cd backend && npm install`
4. Configurar start command: `cd backend && npm start`
5. Agregar variables de entorno:
   - `DB_URI`: URI de MongoDB Atlas
   - `JWT_SECRET`: Clave secreta para JWT (diferente a desarrollo)
   - `FRONTEND_URL`: URL de Netlify/Vercel
   - `NODE_ENV`: production
   - `PORT`: (Render lo asigna automáticamente)

### Frontend (Netlify/Vercel)

1. Crear nuevo site en Netlify
2. Conectar repositorio de GitHub
3. Configurar build settings:
   - Base directory: `client`
   - Build command: `npm run build`
   - Publish directory: `client/dist`
4. Agregar variable de entorno:
   - `VITE_API_URL`: URL del backend en Render

## Arquitectura y decisiones clave

### Backend
- **Autenticación JWT**: Sistema de tokens para autenticación stateless y escalable
- **Bcrypt para passwords**: Hashing seguro de contraseñas con salt automático
- **Middleware de autorización**: Protección de rutas sensibles verificando JWT
- **MongoDB con Mongoose**: Permite esquemas flexibles y validación de datos
- **Modelo de features opcional**: El objeto `features` acepta cualquier combinación de propiedades, permitiendo productos con características diferentes
- **Relaciones entre colecciones**: Pedidos vinculados a usuarios y productos mediante referencias
- **Middleware de logging**: Registra todas las peticiones HTTP para debugging
- **Manejo centralizado de errores**: Middleware global que captura errores y devuelve respuestas JSON consistentes
- **CORS configurado**: Permite requests desde el frontend tanto en desarrollo como producción

### Frontend
- **Context API para estado global**: Dos contextos independientes (Auth y Cart) para gestión de estado
- **Persistencia en localStorage**: Mantiene sesión de usuario y carrito tras recargas
- **Componente ProtectedRoute**: HOC que protege rutas privadas y redirige a login
- **React Router con rutas dinámicas y protegidas**: `/productos/:id` carga productos individuales, `/profile` requiere autenticación
- **JWT en headers**: Todas las peticiones autenticadas envían token en `Authorization: Bearer`
- **UI condicional reactiva**: Header y navegación cambian según estado de autenticación
- **Fetch con AbortController**: Cancela requests cuando el componente se desmonta
- **Optimistic updates**: Actualiza la UI antes de confirmar con el servidor (mejor UX)
- **Componentes reusables**: Separación clara entre componentes de presentación y lógica
- **CSS modular con variables**: Mantiene consistencia visual y facilita temas
- **Formularios controlados**: Todos los inputs manejan estado con React

## Licencia

Este proyecto es de uso académico para el curso de Desarrollo de Aplicaciones Web en ITBA.

## Contacto

Para consultas sobre el proyecto, contactar a los integrantes del equipo a través de GitHub.
