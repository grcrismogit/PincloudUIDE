# Parte 1 — Autenticación y base 🔐

> **Rama de Git:** `parte-1-autenticacion`

Esta es la base sobre la que se monta todo el proyecto: el registro de usuarios,
el inicio de sesión, la verificación por correo y la seguridad con JWT.

---

## 🎯 Qué cubre esta parte

### Funcionalidades
- Registro de cuenta nueva.
- Inicio de sesión (login).
- Verificación de correo con código de 6 dígitos.
- Recuperación de contraseña ("olvidé mi contraseña").
- Protección de rutas con **JWT** (token de sesión).
- Página de inicio (landing) e información.

### Archivos de los que eres responsable

**Backend**
| Archivo | Qué hace |
|---------|----------|
| `server.js` | Punto de entrada del servidor Express |
| `backend/config/db.js` | Conexión a MongoDB |
| `backend/models/User.js` | Modelo de usuario (con contraseña encriptada) |
| `backend/middleware/auth.js` | Verifica el token JWT en cada petición protegida |
| `backend/routes/auth.js` | Rutas: registro, login, verificar email, reset password |
| `backend/services/emailService.js` | Envío de correos con AWS SES |

**Frontend**
| Archivo | Qué hace |
|---------|----------|
| `client/src/context/AuthContext.jsx` | Estado global: si el usuario está logueado |
| `client/src/pages/Home.jsx` | Página de inicio con login/registro |
| `client/src/pages/VerifyEmail.jsx` | Pantalla para meter el código de verificación |
| `client/src/pages/ForgotPassword.jsx` | Recuperación de contraseña en 3 pasos |
| `client/src/pages/Informacion.jsx` | Página informativa pública |
| `client/src/components/PublicNavbar.jsx` | Barra de navegación pública |
| `client/src/utils/helpers.js` | Función `apiFetch` para llamar al backend |

---

## 🔑 Conceptos que debes saber explicar

- **JWT (JSON Web Token):** un "carnet digital" firmado que prueba quién es el
  usuario en cada petición, sin guardar sesión en el servidor.
- **bcrypt:** algoritmo que encripta las contraseñas de forma irreversible.
  La contraseña real nunca se guarda.
- **Middleware:** código que se ejecuta entre la petición y la respuesta;
  aquí se usa para verificar el token antes de dar acceso.

---

## 🌳 Comandos de Git para tu parte

```bash
# 1. Clonar el repositorio (solo la primera vez)
git clone https://github.com/grcrismogit/PincloudUIDE.git
cd PincloudUIDE

# 2. Cambiarte a TU rama
git checkout parte-1-autenticacion

# 3. Cada vez que hagas cambios:
git add .
git commit -m "feat(parte-1): describe brevemente tu cambio"
git push origin parte-1-autenticacion

# 4. Para traer lo último de main a tu rama (mantenerte al día):
git checkout main
git pull origin main
git checkout parte-1-autenticacion
git merge main

# 5. Cuando tu parte esté lista, abre un Pull Request en GitHub
#    desde 'parte-1-autenticacion' hacia 'main'.
```

---

## ✅ Cómo probar que tu parte funciona

1. Levanta el proyecto (ver README principal).
2. Crea una cuenta nueva.
3. Revisa tu correo y mete el código de verificación.
4. Inicia sesión.
5. Prueba "¿Olvidaste tu contraseña?" y verifica el flujo completo.
