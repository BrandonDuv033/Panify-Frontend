# Panify — Frontend

> **"Horneamos Calidad, Entregamos Confianza y Unimos Lazos"**

Aplicación cliente de **Panify**, el sistema de gestión de pedidos, inventario y entregas de la panadería **Distribuciones Oro Pan**. Ofrece una interfaz pública (landing, catálogo, registro e inicio de sesión), un área para clientes y un panel de administración.

---

## 📌 Contexto

| | |
|---|---|
| **Cliente / caso de estudio** | Fabrica de Pan "Distribuciones Oro Pan" |
| **Programa** | SENA — Análisis y Desarrollo de Software (ADSO) |
| **Ficha / Grupo** | 3315796 / Grupo 4 |

**Problema:** los pedidos se toman de forma manual (llamadas y papel), lo que genera pérdida de información, retrasos y falta de comprobantes claros. El frontend ofrece una interfaz web para hacer pedidos, consultar recibos y gestionar la operación.

---

## 🎯 Funcionalidades

| Área | Qué ofrece |
|---|---|
| **Pública** | Landing page con navegación (Inicio, Nosotros, Productos, Contacto, Ingresar), catálogo público de productos, registro de nuevos clientes, inicio de sesión y recuperación de contraseña. |
| **Cliente** | Realizar pedidos mediante carrito de compras, consultar el historial en *Mis pedidos*, visualizar recibos digitales y gestionar el perfil personal (dirección de entrega y teléfono). |
| **Panadero** | **Panel de Producción:** CRUD completo de productos (crear, editar, activar/desactivar), control e ingreso de stock de inventario, consulta de pedidos programados por fecha/día para producción, y cambio de estado del pedido (*Pendiente* ➔ *En preparación* ➔ *Listo*).|
| **Domiciliario** |**Panel de Entregas:** Visualización de pedidos asignados ordenados por prioridad y franja horaria, consulta de detalles del cliente (dirección y barrio), actualización del estado del despacho (*Listo* ➔ *En camino* ➔ *Entregado*) y consulta de rutas de entrega.|
| **Administración** | **Dashboard Global:** Control total del sistema (CRUD de usuarios, asignación de roles y activación/inactivación de cuentas), monitoreo general de inventario con alertas de stock bajo/agotado, gestión global de pedidos y recibos, y generación de reportes operativos (diarios, semanales y mensuales). |


---

## 🛠️ Tecnologías

| Componente | Tecnología |
| :--- | :--- |
| Librería de UI | React |
| Herramienta de desarrollo y build | Vite |
| Maquetación | HTML5 semántico |
| Framework de UI / Estilos | Bootstrap 5 / React-Bootstrap |
| Estilos personalizados | CSS3 (Diseño responsivo) |
| Comunicación con el backend | Capa de servicios (`src/services/`) |
| Control de versiones | Git y GitHub |

---

## 📁 Estructura del proyecto

```
📁 frontend/
├── 📁 public/                     # Archivos estáticos públicos
│   └── 📁 img/                    # Logotipos, favicon y banners estáticos
│
├── 📁 src/                        # Código fuente de la aplicación
│   ├── 📁 assets/                 # Recursos estáticos locales
│   │   ├── 📁 css/                # Estilos organizados por capas
│   │   │   ├── 📁 base/           # variables.css (colores, fuentes), reset.css
│   │   │   ├── 📁 layout/         # navbar.css, sidebar.css, footer.css
│   │   │   ├── 📁 pages/          # Estilos específicos por vista
│   │   │   └── 📁 components/     # Estilos de modales, botones y tablas
│   │   │
│   │   └── 📁 img/                # Imágenes importadas desde componentes
│   │
│   ├── 📁 components/             # Piezas de interfaz reutilizables
│   │   ├── 📁 common/             # Navbar, Footer, RutaProtegida, Boton, Modal
│   │   ├── 📁 cliente/            # TarjetaProducto, CarritoCompras, ResumenPedido
│   │   ├── 📁 panadero/           # TablaProduccion, FormularioInsumo
│   │   ├── 📁 domiciliario/       # TarjetaEntrega, DetalleRuta
│   │   └── 📁 admin/              # TablaUsuarios, TablaRecibos, TarjetaMetrica
│   │
│   ├── 📁 context/                # Estado global de la interfaz
│   │   ├── 📄 AuthContext.jsx     # Estado de sesión (token JWT, rol de usuario, logout)
│   │   └── 📄 CartContext.jsx     # Estado del carrito (agregar/eliminar productos, total)
│   │
│   ├── 📁 hooks/                  # Custom hooks para lógica de UI
│   │   ├── 📄 useAuth.js
│   │   ├── 📄 useCarrito.js
│   │   └── 📄 useModal.js
│   │
│   ├── 📁 layouts/                # Plantillas de estructura
│   │   ├── 📄 PublicLayout.jsx    # Cabecera y pie para visitantes
│   │   ├── 📄 ClienteLayout.jsx   # Barra superior con carrito y perfil de cliente
│   │   └── 📄 DashboardLayout.jsx # Panel con Sidebar adaptativo según el rol
│   │
│   ├── 📁 pages/                  # Vistas cargadas según la ruta
│   │   ├── 📁 public/             # Home, Catalogo, Login, Registro, RecuperarPassword
│   │   ├── 📁 cliente/            # MisPedidos, MiPerfil, Checkout
│   │   ├── 📁 panadero/           # OrdenesProduccion, GestionProductos
│   │   ├── 📁 domiciliario/       # MisEntregas, Rutas
│   │   └── 📁 admin/              # Dashboard, GestionUsuarios, Recibos, Reportes
│   │
│   ├── 📁 routes/                 # Enrutador principal
│   │   ├── 📄 AppRouter.jsx       # Definición de rutas públicas y privadas
│   │   └── 📄 ProtectedRoute.jsx  # Control visual de acceso por roles
│   │
│   ├── 📁 services/               # Consumo de la API
│   │   └── 📄 api.js              # Instancia Axios con interceptor de cabeceras
│   │
│   └── 📁 utils/                  # Formateadores de interfaz
│       ├── 📄 formatearMoneda.js
│       └── 📄 formatearFecha.js
│
├── 📄 index.html                  # Plantilla HTML principal
├── 📄 vite.config.js              # Configuración de Vite
└── 📄 package.json                # Dependencias del proyecto
```

---

## 🚀 Instalación y ejecución

### Requisitos

- Node.js
- Git

### Pasos

```bash
# 1. Clonar el repositorio
git clone <URL-del-repositorio>
cd frontend

# 2. Instalar dependencias
npm install

# 3. Ejecutar en modo desarrollo
npm run dev
```

### Conexión con el backend

La URL base de la API se configura en `src/services/api.js`.

> 🚧 URL y variables de entorno: *por definir* según el backend.

---

## 🌿 Flujo de trabajo en Git

### Ramas de trabajo (Feature Branches)

```
chore/setup-base-ui
feature/auth-login
feature/gestion-usuarios
feature/gestion-productos
feature/gestion-pedidos
feature/gestion-recibos
feature/gestion-entregas
```

### Commits semánticos

Formato: `<tipo>(<ámbito>): <descripción en imperativo y minúsculas, máx. 50 caracteres>`

- **Tipos:** `feat`, `docs`, `style`, `refactor`, `chore`
- **Ámbitos comunes:** `ui`, `repo`, `admin`, `cliente`, `trimestre3`

Ejemplos:

```
docs(repo): agregar readme inicial del frontend
feat(ui): crear componente navbar responsivo
style(ui): definir variables globales de color
```

---

## 👥 Equipo

- Brayan Sneyder Devia Muñoz
- Martín Cruz Muñoz
- Jeison Alejandro Diaz Acosta
- Brandon Duvan Guevara Rodríguez
- Kevin Julian González Chavez
