# Parte 2 — Galería y subida de imágenes a AWS S3 🖼️☁️

> **Rama de Git:** `parte-2-galeria-aws`

Esta parte permite ver la galería de pins y subir imágenes nuevas, que se guardan
en **Amazon S3** (almacenamiento en la nube).

---

## 🎯 Qué cubre esta parte

### Funcionalidades
- Mostrar la galería de pins en cuadrícula tipo "masonry".
- Subir una imagen nueva (pin) con título, descripción y categoría.
- Filtrar por categoría.
- Buscar pins.

### Archivos de los que eres responsable

**Backend**
| Archivo | Qué hace |
|---------|----------|
| `backend/config/aws.js` | Crea el cliente de Amazon S3 |
| `backend/models/Pin.js` | Modelo de pin (título, imagen, autor, categoría) |
| `backend/routes/pins.js` | Rutas: listar pins, generar URL de subida, crear pin |

**Frontend**
| Archivo | Qué hace |
|---------|----------|
| `client/src/pages/Gallery.jsx` | Página principal con la galería |
| `client/src/components/PinCard.jsx` | Tarjeta que muestra cada pin |
| `client/src/components/UploadModal.jsx` | Ventana para subir una imagen |
| `client/src/components/Sidebar.jsx` | Menú lateral de navegación |
| `client/src/components/Topbar.jsx` | Barra superior con búsqueda |
| `client/src/components/CategoryBar.jsx` | Barra de categorías |

---

## 🔑 Conceptos que debes saber explicar

- **Amazon S3:** servicio de almacenamiento de archivos en la nube. Aquí se
  guardan las imágenes de los pins.
- **Presigned URL (URL firmada):** una URL temporal (5 minutos) que genera el
  backend para que el navegador suba la imagen **directamente a S3**, sin
  sobrecargar el servidor.
- **Masonry:** diseño de galería tipo Pinterest, con columnas de altura variable.

### El flujo de subida (importante para la defensa)
1. El usuario elige una imagen en `UploadModal`.
2. El frontend pide al backend una **presigned URL** (`POST /api/pins/presign`).
3. El frontend sube la imagen **directo a S3** usando esa URL.
4. El frontend avisa al backend con la clave del archivo (`POST /api/pins`).
5. El backend guarda el pin en MongoDB.

---

## 🌳 Comandos de Git para tu parte

```bash
# 1. Clonar el repositorio (solo la primera vez)
git clone https://github.com/grcrismogit/PincloudUIDE.git
cd PincloudUIDE

# 2. Cambiarte a TU rama
git checkout parte-2-galeria-aws

# 3. Cada vez que hagas cambios:
git add .
git commit -m "feat(parte-2): describe brevemente tu cambio"
git push origin parte-2-galeria-aws

# 4. Para traer lo último de main a tu rama (mantenerte al día):
git checkout main
git pull origin main
git checkout parte-2-galeria-aws
git merge main

# 5. Cuando tu parte esté lista, abre un Pull Request en GitHub
#    desde 'parte-2-galeria-aws' hacia 'main'.
```

---

## ✅ Cómo probar que tu parte funciona

1. Inicia sesión (necesitas la Parte 1 funcionando).
2. Sube una imagen nueva con título y categoría.
3. Verifica que aparece en la galería.
4. Filtra por categoría y usa el buscador.
