# Parte 3 — Interacción, perfil y moderación con IA ❤️💬🤖

> **Rama de Git:** `parte-3-interaccion-moderacion`

Esta parte da vida social a la app (likes, guardados, comentarios), el perfil del
usuario y la moderación automática de imágenes con inteligencia artificial.

---

## 🎯 Qué cubre esta parte

### Funcionalidades
- Dar/quitar like a un pin.
- Guardar/desguardar pins.
- Comentar en los pins.
- Ver el detalle de un pin en una ventana.
- Página de perfil con los pins guardados.
- Página de explorar por temáticas.
- **Moderación con IA:** rechazo automático de imágenes inapropiadas.
- Envío de correos de notificación.

### Archivos de los que eres responsable

**Backend** (las partes de interacción y moderación dentro de):
| Archivo | Qué hace |
|---------|----------|
| `backend/routes/pins.js` | Rutas de like, guardar, comentar, eliminar |
| `backend/config/aws.js` | Clientes de SES (correo) y Rekognition (moderación) |

**Frontend**
| Archivo | Qué hace |
|---------|----------|
| `client/src/components/DetailModal.jsx` | Ventana de detalle del pin con comentarios |
| `client/src/pages/Profile.jsx` | Perfil del usuario y pins guardados |
| `client/src/pages/Explorar.jsx` | Explorar pins por categorías |

> ⚠️ Nota: `pins.js` y `aws.js` los compartes con la Parte 2. Coordínate con tu
> compañero/a: tú trabajas las rutas de like/guardar/comentar/moderación y la
> configuración de SES + Rekognition.

---

## 🔑 Conceptos que debes saber explicar

- **AWS Rekognition:** servicio de IA que analiza imágenes. Aquí detecta
  contenido inapropiado (`DetectModerationLabels`) con 70% de confianza mínima.
  Si la imagen es inapropiada, se borra de S3 y se rechaza el pin.
- **AWS SES (Simple Email Service):** servicio para enviar correos.
- **Actualización optimista:** cuando das like, la interfaz se actualiza al
  instante sin esperar al servidor (mejor experiencia de usuario).

---

## 🌳 Comandos de Git para tu parte

```bash
# 1. Clonar el repositorio (solo la primera vez)
git clone https://github.com/grcrismogit/PincloudUIDE.git
cd PincloudUIDE

# 2. Cambiarte a TU rama
git checkout parte-3-interaccion-moderacion

# 3. Cada vez que hagas cambios:
git add .
git commit -m "feat(parte-3): describe brevemente tu cambio"
git push origin parte-3-interaccion-moderacion

# 4. Para traer lo último de main a tu rama (mantenerte al día):
git checkout main
git pull origin main
git checkout parte-3-interaccion-moderacion
git merge main

# 5. Cuando tu parte esté lista, abre un Pull Request en GitHub
#    desde 'parte-3-interaccion-moderacion' hacia 'main'.
```

---

## ✅ Cómo probar que tu parte funciona

1. Inicia sesión y entra a la galería (necesitas Partes 1 y 2).
2. Dale like y guarda algunos pins.
3. Abre un pin y deja un comentario.
4. Ve a tu perfil y revisa los pins guardados.
5. Intenta subir una imagen inapropiada → debe ser rechazada por la IA.
