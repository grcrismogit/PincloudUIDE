# PinCloud ☁️📌

Aplicación web estilo Pinterest. Permite registrarse, subir imágenes ("pins"),
explorarlas, guardarlas, darles like y comentar. Construida con **React + Vite**
(frontend), **Node.js + Express** (backend), **MongoDB** (base de datos) y
**AWS** (S3 para imágenes, SES para correos, Rekognition para moderación).

**Repositorio:** https://github.com/grcrismogit/PincloudUIDE

---

## ⚡ Conexión rápida (LÉEME PRIMERO)

> Copia y pega estos comandos tal cual. No hay que pensar.

### 1️⃣ La PRIMERA vez — conectarte al repositorio
```bash
git clone https://github.com/grcrismogit/PincloudUIDE.git
cd PincloudUIDE
```

### 2️⃣ Cámbiate a TU rama (según quién seas)
```bash
# 👤 Persona 1 (Autenticación):
git checkout parte-1-autenticacion

# 👤 Persona 2 (Galería y AWS):
git checkout parte-2-galeria-aws

# 👤 Persona 3 (Interacción y moderación):
git checkout parte-3-interaccion-moderacion
```

### 3️⃣ Para SUBIR tus cambios (siempre los mismos 3 comandos)
```bash
git add .
git commit -m "escribe aqui que cambiaste"
git push
```

### 4️⃣ Para BAJAR lo último que subieron los demás
```bash
git pull
```

> Cada quien lee su guía detallada en la carpeta [`docs/`](docs/).

---

## 👥 Equipo y división del proyecto

| Parte | Integrante | Área | Rama | Guía |
|-------|-----------|------|------|------|
| 1 | _(tu nombre)_     | Autenticación (login, registro, JWT, email) | `parte-1-autenticacion` | [docs/PARTE-1-AUTENTICACION.md](docs/PARTE-1-AUTENTICACION.md) |
| 2 | _(compañero 2)_   | Galería y subida a AWS S3 | `parte-2-galeria-aws` | [docs/PARTE-2-GALERIA-AWS.md](docs/PARTE-2-GALERIA-AWS.md) |
| 3 | _(compañero 3)_   | Interacción, perfil y moderación con IA | `parte-3-interaccion-moderacion` | [docs/PARTE-3-INTERACCION-MODERACION.md](docs/PARTE-3-INTERACCION-MODERACION.md) |

---

## 🌳 Árbol de subida a Git

Usamos **una rama por integrante** que sale de `main`. Cada quien sube su parte
a su rama y luego se une (merge) a `main` mediante un Pull Request:

```
                    o  parte-1-autenticacion   (Persona 1)
                   /
  main  o--------o--------o   <--- aquí se unen las 3 partes
                   \
                    o  parte-2-galeria-aws      (Persona 2)
                     \
                      o  parte-3-interaccion    (Persona 3)
```

- `main` → rama principal, siempre debe funcionar.
- Cada rama de parte → donde trabaja una persona sin pisar a las demás.

---

## 🚀 Cómo levantar el proyecto en tu computadora

### Requisitos previos
- [Node.js](https://nodejs.org) (versión 18 o superior)
- Una cuenta de [MongoDB Atlas](https://www.mongodb.com/atlas) (gratis)
- Credenciales de AWS (S3, SES, Rekognition)

### 1. Configurar variables de entorno
Copia el archivo de ejemplo y rellena tus datos reales:
```bash
cp .env.example .env
```
Luego abre `.env` y completa: `MONGO_URI`, `JWT_SECRET`, claves de `AWS`, etc.

> ⚠️ **NUNCA subas el archivo `.env` a GitHub.** Ya está protegido en `.gitignore`.

### 2. Instalar dependencias
```bash
# Backend (en la carpeta raíz)
npm install

# Frontend
cd client
npm install
cd ..
```

### 3. Ejecutar en modo desarrollo
Necesitas **dos terminales** abiertas:

```bash
# Terminal 1 — Backend (puerto 3000)
npm run dev
```
```bash
# Terminal 2 — Frontend (puerto 5173)
cd client
npm run dev
```
Abre tu navegador en **http://localhost:5173**

### 4. Compilar para producción
```bash
npm run build   # compila el frontend dentro de client/dist
npm start       # arranca el servidor que sirve todo junto
```

---

## 📁 Estructura del proyecto

```
PincloudUIDE/
├── server.js               # Punto de entrada del backend (Express)
├── package.json            # Dependencias y comandos del backend
├── .env.example            # Plantilla de variables de entorno
├── backend/
│   ├── config/
│   │   ├── db.js           # Conexión a MongoDB
│   │   └── aws.js          # Clientes de AWS (S3, SES, Rekognition)
│   ├── models/
│   │   ├── User.js         # Modelo de usuario
│   │   └── Pin.js          # Modelo de pin
│   ├── middleware/
│   │   └── auth.js         # Verificación del token JWT
│   ├── routes/
│   │   ├── auth.js         # Rutas de login/registro/verificación
│   │   └── pins.js         # Rutas de pins (subir, like, comentar...)
│   └── services/
│       └── emailService.js # Envío de correos con AWS SES
└── client/                 # Aplicación React (Vite)
    ├── index.html
    └── src/
        ├── main.jsx        # Punto de entrada de React
        ├── App.jsx         # Definición de rutas
        ├── index.css       # Estilos globales
        ├── context/        # Estado global (autenticación)
        ├── components/     # Piezas reutilizables (Sidebar, PinCard...)
        ├── pages/          # Páginas (Home, Gallery, Profile...)
        └── utils/          # Funciones auxiliares (fetch, formato...)
```

---

## 🧰 Tecnologías

| Capa | Tecnología |
|------|-----------|
| Frontend | React 18, Vite, React Router |
| Backend | Node.js, Express |
| Base de datos | MongoDB + Mongoose |
| Autenticación | JWT, bcrypt |
| Almacenamiento | AWS S3 |
| Correos | AWS SES |
| Moderación de imágenes | AWS Rekognition |
