# e-Race VW Group: configuración estable con Firebase

Esta versión elimina PeerJS/WebRTC. Todos los equipos se sincronizan mediante Firebase Realtime Database.

## 1. Crear proyecto gratis
1. Abre https://console.firebase.google.com/
2. Pulsa **Crear un proyecto**.
3. Nombre sugerido: `e-race-vw`.
4. Google Analytics es opcional.

## 2. Crear aplicación web
1. Dentro del proyecto, pulsa el icono `</>` para agregar una app web.
2. Nombre sugerido: `e-race-web`.
3. No es necesario activar Firebase Hosting, porque el sitio permanece en GitHub Pages.
4. Copia el objeto `firebaseConfig`.
5. Abre `firebase-config.js` y sustituye todos los valores `REEMPLAZAR`.

## 3. Activar inicio anónimo
1. Firebase Console > Authentication > Comenzar.
2. Sign-in method / Proveedores de acceso.
3. Activa **Anónimo** y guarda.

## 4. Crear Realtime Database
1. Firebase Console > Build > Realtime Database.
2. Pulsa **Crear base de datos**.
3. Elige una región cercana a México disponible.
4. Selecciona modo bloqueado.
5. En la pestaña **Reglas**, pega el contenido de `database.rules.json` y pulsa **Publicar**.
6. Copia la URL de la base de datos y confirma que sea idéntica a `databaseURL` en `firebase-config.js`.

## 5. Subir a GitHub
Reemplaza en tu repositorio estos tres archivos:
- `index.html`
- `app.js`
- `firebase-config.js`

No necesitas modificar `styles.css`.

## 6. Probar
1. Confirma que GitHub Actions termine en verde.
2. Abre la página y pulsa Ctrl+F5.
3. En laptop elige Crear carrera.
4. En celular escanea el QR.
5. Debe mostrar Conectado y permitir avatar/nombre.

## Seguridad práctica
Las reglas requieren autenticación anónima, pero cualquier usuario autenticado del proyecto puede acceder a las salas si conoce el código. Para sesiones internas cortas es una base funcional. El host elimina la sala automáticamente cuando cierra la página, siempre que la desconexión sea detectada.
