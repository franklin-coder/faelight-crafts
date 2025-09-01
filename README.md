
# FaeLight Crafts - E-commerce Website

Réplica personalizada del sitio web Plumeria Jewels para FaeLight Crafts, la marca de joyas artesanales de Julia en Victoria, Canadá.

## 🚀 Instrucciones para Ejecutar Localmente

### Prerequisitos
- Node.js (versión 18 o superior)
- Yarn o npm
- Git

### 1. Clonar y Configurar el Proyecto

```bash
# Si descargas el proyecto completo
cd ruta/donde/descargaste/faelight_crafts

# Navegar a la carpeta de la aplicación
cd app

# Instalar dependencias
yarn install
# o si usas npm:
# npm install
```

### 2. Configurar Variables de Entorno

Crea un archivo `.env.local` en la carpeta `app/` con el siguiente contenido:

```bash
# Base de datos Supabase
DATABASE_URL="postgresql://postgres:[TU-PASSWORD]@db.znwfavxqufsrafyxhqvw.supabase.co:5432/postgres"

# NextAuth (para autenticación - opcional)
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="tu-clave-secreta-aqui"

# Stripe (para pagos)
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY="pk_test_tu_clave_publica_stripe"
STRIPE_SECRET_KEY="sk_test_tu_clave_secreta_stripe"
STRIPE_WEBHOOK_SECRET="whsec_tu_webhook_secret"

# URL base para desarrollo
NEXT_PUBLIC_BASE_URL="http://localhost:3000"
```

### 3. Configurar Base de Datos (Opcional)

Si quieres usar la base de datos:

```bash
# Generar cliente Prisma
npx prisma generate

# Ejecutar migraciones
npx prisma db push

# Poblar base de datos con datos de ejemplo
npx prisma db seed
```

### 4. Ejecutar en Modo Desarrollo

```bash
# Iniciar servidor de desarrollo
yarn dev
# o si usas npm:
# npm run dev
```

La aplicación estará disponible en: **http://localhost:3000**

### 5. Para Producción

```bash
# Construir para producción
yarn build

# Ejecutar versión de producción
yarn start
```

## 📦 Gestión de Productos

Los productos se gestionan a través de archivos JSON para facilitar las actualizaciones. 

### Archivo Principal de Productos
Los productos están en: `app/data/products.json`

### Estructura de un Producto

```json
{
  "id": "producto-001",
  "name": "Nombre del Producto",
  "price": 25.00,
  "description": "Descripción corta para catálogo",
  "longDescription": "Descripción detallada para la página del producto...",
  "category": "necklaces|earrings|bracelets|rings|accessories",
  "images": [
    "url-imagen-1.jpg",
    "url-imagen-2.jpg"
  ],
  "featured": true,
  "inStock": true,
  "materials": ["Material 1", "Material 2"],
  "dimensions": "Dimensiones del producto",
  "care_instructions": "Instrucciones de cuidado",
  "created_at": "2024-01-15T10:00:00Z",
  "updated_at": "2024-01-15T10:00:00Z"
}
```

### ✅ Cómo Agregar un Producto

1. Abre el archivo `app/data/products.json`
2. Agrega el nuevo producto al array siguiendo la estructura mostrada arriba
3. Asegúrate de usar un `id` único
4. Las imágenes pueden ser URLs externas o rutas locales a `/images/products/`
5. Guarda el archivo
6. La aplicación se actualizará automáticamente en desarrollo

**Ejemplo de producto nuevo:**

```json
{
  "id": "anillo-nuevo-001",
  "name": "Anillo de Plata Artesanal",
  "price": 45.00,
  "description": "Anillo de plata 925 hecho a mano con piedras naturales",
  "longDescription": "Este hermoso anillo artesanal está crafteado en plata 925 con técnicas tradicionales...",
  "category": "rings",
  "images": [
    "/images/products/anillo-nuevo-1.jpg",
    "/images/products/anillo-nuevo-2.jpg"
  ],
  "featured": false,
  "inStock": true,
  "materials": ["Plata 925", "Piedra turquesa", "Acabado mate"],
  "dimensions": "Tallas disponibles: 6-9",
  "care_instructions": "Limpiar con paño suave. Evitar contacto con químicos.",
  "created_at": "2024-08-17T12:00:00Z",
  "updated_at": "2024-08-17T12:00:00Z"
}
```

### ❌ Cómo Eliminar un Producto

1. Abre el archivo `app/data/products.json`
2. Encuentra el producto que quieres eliminar por su `id`
3. Elimina todo el objeto del producto (desde `{` hasta `}` incluyendo la coma si no es el último)
4. Guarda el archivo
5. La aplicación se actualizará automáticamente

### 🔄 Cómo Actualizar un Producto

1. Abre el archivo `app/data/products.json`
2. Encuentra el producto por su `id`
3. Modifica los campos que necesites
4. Actualiza el campo `updated_at` con la fecha actual
5. Guarda el archivo

### 📷 Gestión de Imágenes

Para agregar imágenes de productos:

1. **Opción 1 - URLs externas:** Usa URLs directas de imágenes en internet
2. **Opción 2 - Imágenes locales:** 
   - Coloca las imágenes en `app/public/images/products/`
   - Referéncialas como `"/images/products/nombre-imagen.jpg"`

### Categorías Disponibles
- `necklaces` - Collares
- `earrings` - Aretes
- `bracelets` - Pulseras  
- `rings` - Anillos
- `accessories` - Accesorios

### 🎨 Personalización de Marca

#### Colores del Sitio
Los colores están definidos en `app/tailwind.config.js`:
- Verde principal: `#0A8E81`
- Negro: `#000000`
- Gris verdoso: `#AEBBB2`
- Beige claro: `#FAF5EF`

#### Logo
El logo está en `app/public/images/logo/` y se puede reemplazar manteniendo el mismo nombre de archivo.

## 💳 Configuración de Stripe

Para habilitar pagos reales:

1. Crea una cuenta en [Stripe](https://stripe.com)
2. Obtén tus claves API del dashboard
3. Actualiza las variables de entorno con tus claves reales
4. Configura webhooks en Stripe apuntando a tu dominio

## 🔧 Estructura del Proyecto

```
app/
├── components/     # Componentes React reutilizables
├── pages/         # Páginas de Next.js
├── public/        # Archivos estáticos (imágenes, favicon, etc.)
├── data/          # Archivos JSON de productos y configuración
├── styles/        # Estilos CSS
├── lib/           # Utilidades y configuraciones
└── prisma/        # Configuración de base de datos
```

## 📱 Soporte

Para modificaciones avanzadas o problemas técnicos, consulta la documentación de:
- [Next.js](https://nextjs.org/docs)
- [React](https://react.dev)
- [Tailwind CSS](https://tailwindcss.com/docs)
- [Stripe](https://stripe.com/docs)

---

**FaeLight Crafts** - Artesanía única desde Victoria, Canadá 🍁
