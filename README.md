# 🏋️ Gym Offline

Una **PWA (Progressive Web App)** minimalista para llevar tu diario de entrenamiento en el gimnasio, diseñada para funcionar **100% sin conexión a internet**. Ideal para gimnasios sin WiFi ni cobertura móvil (sótanos, salas insonorizadas, etc.).

Todo el proyecto vive en un **único archivo `index.html`**, sin dependencias externas, sin frameworks, sin servidores y sin necesidad de crear una cuenta.

---

## 📋 Índice

- [Características](#-características)
- [¿Por qué funciona sin internet?](#-por-qué-funciona-sin-internet)
- [Tecnologías utilizadas](#-tecnologías-utilizadas)
- [Instalación y uso](#-instalación-y-uso)
- [Mi uso](#-mi-uso)
- [Cómo usar la aplicación](#-cómo-usar-la-aplicación)
- [Almacenamiento de datos](#-almacenamiento-de-datos)
- [Privacidad](#-privacidad)
- [Estructura del proyecto](#-estructura-del-proyecto)
- [Limitaciones conocidas](#-limitaciones-conocidas)
- [Contribuir](#-contribuir)
- [Licencia](#-licencia)

---

## ✨ Características

- **📅 Gestión de rutinas**: rutinas predefinidas por día (Pecho/Tríceps, Espalda/Bíceps, Piernas/Hombros, Core/Full Body), totalmente editables.
- **🔀 Reordenamiento por arrastre (Drag & Drop)** de rutinas, compatible con gestos táctiles.
- **➕ Creación y edición** de rutinas y ejercicios personalizados.
- **▶️ Modo entrenamiento activo**:
  - Cronómetro de duración de la sesión.
  - Referencia automática de tu última marca (peso/reps) en cada ejercicio.
  - Botones rápidos `+`/`−` para ajustar peso (incrementos de 1.25 kg) y repeticiones.
  - Marca series completadas y lanza automáticamente el descanso.
- **⏱️ Temporizador de descanso flotante**:
  - Configurado por defecto a 90 segundos.
  - Alertas visuales (anillo pulsante) y sonoras generadas con **Web Audio API** (no usa archivos MP3).
  - Vibración háptica al finalizar el descanso (`navigator.vibrate`).
  - Opciones para restar 15 segundos o saltar el descanso.
- **📊 Historial de entrenamientos**: duración, volumen total (kg × reps) y desglose por serie/ejercicio.
- **📚 Biblioteca de ejercicios**: +20 ejercicios predefinidos clasificados por grupo muscular, con opción de crear los tuyos y renombrar los existentes.
- **📈 Evolución por ejercicio**: visualiza el progreso histórico de pesos y repeticiones máximas.

---

## 🌐 ¿Por qué funciona sin internet?

Este proyecto es **100% offline por diseño**:

- No realiza ninguna petición de red (fetch, axios, APIs externas, CDNs, fuentes externas, etc.).
- No requiere backend, base de datos en la nube ni sistema de login.
- Todo el HTML, CSS y JavaScript está **autocontenido en el propio archivo `index.html`**.
- Los datos se guardan directamente en el navegador del dispositivo (ver sección Almacenamiento de datos).

Esto la hace perfecta para usarla en el gimnasio, aunque no haya WiFi ni señal de datos móviles.

---

## 🛠️ Tecnologías utilizadas

Arquitectura **Zero-Dependency** (cero dependencias externas):

- **HTML5** — estructura semántica con metaetiquetas específicas para PWA (`apple-mobile-web-app-capable`, `viewport-fit=cover`).
- **CSS3 puro** — clases utilitarias propias (estilo Tailwind), variables `env(safe-area-inset-*)` para compatibilidad con notch, animaciones con `@keyframes`.
- **JavaScript (ES6+ Vanilla)** — sin frameworks (sin React, Vue ni Angular), manipulación del DOM con eventos delegados.
- **Web Audio API** — generación procedural de los pitidos del temporizador (sin archivos de audio).
- **Vibration API** — feedback háptico al terminar el descanso.
- **localStorage** — persistencia de datos en el dispositivo.

> No se usa ninguna librería externa ni CDN. Todo el código (incluidos los iconos, en formato emoji) está dentro del `index.html`.

---

## 🚀 Instalación y uso

### Opción 1: Abrir directamente el archivo

1. Clona o descarga este repositorio con el comando: `git clone https://github.com/tu-usuario/tu-repositorio.git`
2. Entra en la carpeta del proyecto: `cd tu-repositorio`
3. Abre el archivo `index.html` con cualquier navegador moderno (Chrome, Safari, Firefox, Edge), haciendo doble clic sobre él.
4. ¡Listo! Ya puedes empezar a entrenar.

### Opción 2: Instalarla como App (recomendado)

Para tener una experiencia similar a una app nativa en tu móvil:

**En iOS (Safari):**
1. Abre `index.html` en Safari (puedes subirlo a un hosting gratuito como GitHub Pages, o abrirlo localmente).
2. Pulsa el botón de compartir 🔗.
3. Selecciona **"Añadir a pantalla de inicio"**.

**En Android (Chrome):**
1. Abre `index.html` en Chrome.
2. Pulsa el menú (⋮) y selecciona **"Añadir a pantalla de inicio"** o **"Instalar aplicación"**.

> 💡 **Tip:** Si publicas este repositorio con **GitHub Pages**, podrás instalar la app desde una URL pública y seguirá funcionando sin conexión una vez cargada la primera vez.

---

## 📱 Mi uso

Este es el método que utilizo personalmente en el día a día, aprovechando la app **Atajos (Shortcuts)** de iPhone para lanzar la aplicación de forma rápida y directa, sin depender de conexión a internet:

1. Abro la app **Atajos** en mi iPhone.
2. Creo (o ejecuto) un atajo que utiliza la acción **"Obtener archivo de"**, apuntando al archivo `index.html` guardado localmente en el dispositivo (por ejemplo, en la app Archivos/iCloud Drive).
3. A continuación, añado la acción **"Mostrar vista web"**, pasándole como entrada el archivo obtenido en el paso anterior.
4. Ejecuto el atajo y Safari abre el archivo `index.html` directamente en una vista web, funcionando exactamente igual que la aplicación completa, sin necesidad de WiFi ni datos móviles.
5. Para mayor comodidad, añado el atajo a la pantalla de inicio del iPhone, de forma que abrir "Gym Offline" es tan rápido como pulsar un icono más.

> 💡 Esta forma de uso es ideal si no quieres depender de tener el archivo abierto manualmente desde Archivos cada vez, y quieres un acceso directo tipo "app" sin necesidad de subir el proyecto a ningún hosting.

---

## 📖 Cómo usar la aplicación

1. **Elige o crea una rutina** en la pestaña **📅 Rutinas**. Puedes usar las predefinidas o crear las tuyas, añadiendo ejercicios desde el selector con filtro por grupo muscular.
2. **Inicia el entrenamiento** pulsando **▶️ Iniciar** en la rutina elegida.
3. **Registra tus series**: ajusta peso y repeticiones con `+`/`−`, y pulsa `✓` al completar cada serie (esto activa automáticamente el descanso).
4. **Finaliza la sesión** con **✔ Finalizar entrenamiento**. Tus datos se guardan automáticamente.
5. **Consulta tu progreso** en **📊 Historial** (sesiones pasadas) o en **📚 Ejercicios** (evolución por movimiento).

---

## 💾 Almacenamiento de datos

Todos los datos se guardan en el `localStorage` del navegador, bajo la clave `gymoffline_data_v10`:

| Clave | Descripción |
|---|---|
| `activeSession` | Estado del entrenamiento en curso (permite recuperar la sesión si cierras la app por error). |
| `history` | Historial de sesiones finalizadas (máximo 200 entradas). |
| `lastPerformance` | Última marca (peso/reps) usada en cada ejercicio, para referencia rápida. |
| `routines` | Rutinas configuradas (orden, nombres y ejercicios asignados). |
| `customExercises` | Ejercicios creados por el usuario. |
| `nameOverrides` | Nombres personalizados aplicados a ejercicios existentes. |

> ⚠️ **Importante:** Como los datos se guardan en el navegador local, si borras el caché/datos del navegador o cambias de dispositivo, **perderás tu historial**. Actualmente no existe función de exportación/backup automático.

---

## 🔒 Privacidad

- No hay servidores, ni cuentas, ni analíticas, ni cookies de terceros.
- No se envía ningún dato fuera de tu dispositivo.
- Toda tu información de entrenamiento es **exclusivamente tuya** y permanece en tu teléfono/navegador.

---

## 📁 Estructura del proyecto

- `index.html` → Aplicación completa (HTML + CSS + JS en un solo archivo)
- `README.md` → Este documento

---

## ⚠️ Limitaciones conocidas

- No incluye Service Worker ni `manifest.json`, por lo que la instalación como PWA depende de las capacidades básicas del navegador ("Añadir a pantalla de inicio").
- Al depender de `localStorage`, los datos no se sincronizan entre dispositivos ni se respaldan en la nube.
- Diseño optimizado principalmente para móvil (no pensado para escritorio).

---

## 🤝 Contribuir

¿Tienes ideas para mejorar la app? ¡Las contribuciones son bienvenidas!

1. Haz un fork del repositorio.
2. Crea una rama con tu mejora: `git checkout -b mejora/nueva-funcionalidad`
3. Haz commit de tus cambios: `git commit -m 'Añade nueva funcionalidad'`
4. Sube la rama: `git push origin mejora/nueva-funcionalidad`
5. Abre un Pull Request.

---

## 📄 Licencia

Este proyecto puede distribuirse libremente.

---

**Hecho para entrenar sin excusas, con o sin WiFi. 💪**