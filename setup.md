# 🚀 SETUP DEL PROYECTO - Instrucciones Paso a Paso

## ⚡ INSTALACIÓN RÁPIDA (5 minutos)

### 1. Crear proyecto y dependencias
```bash
mkdir proyecto-crud-mongodb
cd proyecto-crud-mongodb
npm init -y
npm install express mongoose dotenv cors bcryptjs jsonwebtoken
npm install --save-dev nodemon
```

### 2. Crear estructura de carpetas
```bash
mkdir -p src/{models,controllers,routes,db,middleware}
mkdir scripts
```

### 3. Copiar todos los archivos
- Copiar cada archivo en su ubicación correspondiente
- Asegurarse de mantener la estructura exacta

### 4. Configurar variables de entorno
- Crear archivo `.env` en la raíz
- Configurar tu MONGO_URI (local o Atlas)

### 5. Instalar y probar
```bash
# Cargar datos de prueba
npm run seed

# Iniciar servidor
npm run dev
```

---

## 📋 TESTING RÁPIDO CON POSTMAN

### 1. Verificar servidor (GET)
```
GET http://localhost:5000/
```
**Debe devolver:** Info de la API con endpoints

### 2. Crear categoría (POST)
```
POST http://localhost:5000/api/categories
Content-Type: application/json

{
  "name": "Bebidas",
  "description": "Jugos y smoothies"
}
```

### 3. Registrar usuario (POST)
```
POST http://localhost:5000/api/auth/register
Content-Type: application/json

{
  "name": "Test User",
  "email": "test@test.com",
  "password": "123456",
  "role": "user"
}
```
**Copiar el token de la respuesta**

### 4. Login (POST)
```
POST http://localhost:5000/api/auth/login
Content-Type: application/json

{
  "email": "admin@test.com",
  "password": "123456"
}
```
**Copiar el token de la respuesta**

### 5. Crear producto con token (POST)
```
POST http://localhost:5000/api/products
Content-Type: application/json
Authorization: Bearer TU_TOKEN_AQUI

{
  "name": "Producto Test",
  "description": "Producto de prueba",
  "category": "ID_DE_CATEGORIA_CREADA",
  "ingredients": ["ingrediente 1", "ingrediente 2"],
  "instructions": ["paso 1", "paso 2"],
  "price": 100
}
```

### 6. Verificar populate (GET)
```
GET http://localhost:5000/api/products
```
**Debe mostrar:** Productos con datos completos de category y createdBy

---

## ✅ CHECKLIST DE VERIFICACIÓN

### ✅ Requisitos Obligatorios:
- [ ] 3 Modelos: Product, User, Category
- [ ] Controladores con lógica CRUD
- [ ] Rutas para cada entidad
- [ ] Populate funciona (Product → Category)
- [ ] Conexión MongoDB
- [ ] Variables .env
- [ ] Estructura src/

### ✅ Requisitos Opcionales:
- [ ] bcrypt encripta contraseñas automáticamente
- [ ] JWT login funciona
- [ ] Rutas protegidas requieren token

### ✅ Testing Funcional:
- [ ] Servidor arranca sin errores
- [ ] Seed carga datos correctamente
- [ ] CRUD básico funciona
- [ ] Login devuelve token válido
- [ ] Token permite crear productos
- [ ] Populate muestra relaciones

---

## 🚨 SOLUCIÓN DE PROBLEMAS

### "Cannot find module"
```bash
npm install
```

### "MongoDB connection failed"
- Verificar MONGO_URI en .env
- Para MongoDB local: verificar que esté corriendo
- Para Atlas: verificar credenciales y whitelist IP

### "JWT token invalid"
- Verificar JWT_SECRET en .env
- Copiar token completo del login
- Usar formato: `Authorization: Bearer TOKEN`

### "Validation failed"
```bash
npm run seed  # Recargar datos limpios
```

---

## 🎯 ESTRUCTURA FINAL

```
proyecto-crud-mongodb/
├── package.json
├── app.js
├── .env
└── src/
    ├── models/
    │   ├── productModel.js
    │   ├── userModel.js
    │   └── categoryModel.js
    ├── controllers/
    │   ├── productController.js
    │   ├── userController.js
    │   ├── categoryController.js
    │   └── authController.js
    ├── routes/
    │   ├── productRoute.js
    │   ├── userRoute.js
    │   ├── categoryRoute.js
    │   └── authRoute.js
    ├── middleware/
    │   └── verifyToken.js
    └── db/
        └── conexion.js
└── scripts/
    └── seedData.js
```

¡Proyecto listo para usar y explicar en clase! 🚀