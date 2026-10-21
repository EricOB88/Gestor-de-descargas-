# Gestor de descargas (PWA)

App web instalable para descargar archivos desde un enlace: pega la URL, analízala, ponle nombre y descárgala. Sin dependencias ni paso de compilación.

## Funciones

- Análisis del enlace: tamaño, tipo, nombre sugerido y soporte de pausa.
- Nombre editable y, en Chrome/Edge de escritorio, elección de la carpeta de destino.
- Pausar y reanudar cuando el servidor admite `Range`.
- Cola con descargas simultáneas configurables, velocidad y tiempo restante.
- Reintentos automáticos, historial y varios enlaces a la vez.
- Notificación al terminar y pantalla encendida durante la descarga.
- Instalable y receptora del menú Compartir en Android.

## Publicar con GitHub Pages

1. Sube este contenido a un repositorio (rama `main`).
2. En **Settings → Pages → Build and deployment → Source**, elige **GitHub Actions**.
3. Cada `push` a `main` publica la app en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.

Alternativa sin Actions: en **Source** elige **Deploy from a branch**, rama `main`, carpeta `/ (root)`, y borra `.github/workflows/pages.yml`.

## Desarrollo local

Necesita servirse por HTTP (el service worker no funciona con `file://`):

```bash
python3 -m http.server 8000
```

Abre `http://localhost:8000`.

## Limitaciones

- **CORS:** si el servidor del archivo no permite peticiones desde otros orígenes, la app no puede analizarlo ni pausarlo; ofrece abrirlo en el navegador.
- **Sin elegir ubicación** el archivo se acumula en memoria hasta terminar, así que para archivos muy grandes usa Chrome/Edge de escritorio y elige carpeta.
- Si se cierra la app durante una descarga, queda como interrumpida y se reinicia desde cero.
- Tras cambiar archivos, sube el número de `V` en `sw.js` para refrescar la caché de los usuarios.

## Licencia

MIT
