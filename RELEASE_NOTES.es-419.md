[English](RELEASE_NOTES.md) | [简体中文](RELEASE_NOTES.zh-CN.md) | Español

# Notas de la versión — Smooth Motion SM86 0.4.6 (refuerzo de fiabilidad)

> **Nota de empaquetado:** en la versión v0.4.3, el recurso portátil del runtime sigue
> siendo `SmoothMotionSM86-0.4.2-win64.zip`; v0.4.3 es una actualización del
> instalador/presentación sobre el motor 0.4.2 sin cambios. El nombre del recurso es
> intencional, no está desactualizado.

## Niveles de evidencia (lee esto primero)

El proyecto los mantiene distintos y nunca los fusiona:

- **D3D11 — ruta en vivo validada instrumentalmente.** Se validó la operación en vivo
  ON/OFF/ON en la configuración dorada con instrumentación del runtime.
- **D3D12 — observado funcionando en juegos reales, instrumentación del motor activo
  no concluyente.** Smooth Motion se observa funcionando en juegos D3D12 reales, pero la
  instrumentación actual del runtime del motor dinámico es **no concluyente** porque no
  se observó tráfico de carga del módulo objetivo en la ventana más reciente de
  validación del motor activo. Esto **no** se clasifica como una regresión.
- **Vulkan — experimental.** Sin interruptor dentro del juego.

Fuente canónica: [VALIDATION.md](VALIDATION.md).

## Novedades de la 0.4.6

- **Refuerzo de fiabilidad.** El Administrador arranca y falla de forma segura en sistemas no
  compatibles o inusuales (controladores desconocidos/no compatibles, configuraciones híbridas y
  multi-GPU, ajustes corruptos), mostrando un estado de compatibilidad claro en lugar de un error.
- **Compatibilidad de fuente única.** El estado y la disponibilidad del backend provienen de un
  único motor; un entorno no compatible o desconocido no puede activar el backend.
- **Paquete de soporte.** "Crear paquete de soporte" genera un ZIP local revisado en cuanto a
  privacidad (sin telemetría) para adjuntar a un issue.
- **Validación de empaquetado.** Las compilaciones de código fuente, onedir, portátil e instalada
  se prueban de forma independiente.

## Novedades de la 0.4.5

- **Corrección de inicio del Administrador.** Se corrigió un fallo de inicio de la GUI
  (`unknown option "-command"`) que podía impedir que el Administrador se abriera.
- **Fallo seguro en cualquier sistema.** El Administrador ahora arranca y sigue siendo útil
  aunque Smooth Motion no pueda activarse (GPU o controlador no compatibles, sistemas
  inusuales o multi-GPU): muestra el entorno detectado y un estado de compatibilidad claro
  en lugar de un error.
- **Red de seguridad de inicio.** Registro de inicio y un diálogo de error amigable (con un
  ID de error y un registro local) en lugar de trazas sin procesar.

## Novedades de la 0.4.4

- **Localización completa: English, 简体中文 y Español.**
- **Administrador / lanzador** — un selector de idioma en el encabezado; el cambio se
  aplica de inmediato y la elección se guarda. La primera ejecución sigue el idioma de
  la interfaz de Windows.
- **Instalador** — English / 简体中文 / Español, elegido desde el idioma de la interfaz
  de Windows o el cuadro de diálogo de idioma; el idioma elegido se traslada al
  Administrador en la primera ejecución.
- **Bandeja del sistema, notificaciones de Windows y la CLI** usan el idioma
  seleccionado (el JSON legible por máquina permanece neutral en cuanto al idioma).
- **Documentación pública** — README, guía de instalación, solución de problemas,
  soporte, compatibilidad, FAQ, hoja de ruta, validación, privacidad, seguridad y el
  EULA están disponibles en los tres idiomas.

## Novedades de la 0.4.3

- **Nueva página de compatibilidad del sistema en el instalador.** Antes de instalar
  nada, el programa de instalación ahora muestra la **GPU**, el **controlador NVIDIA**,
  la **arquitectura** detectados y un estado de compatibilidad en lenguaje sencillo:
  - `Compatible` (configuración validada),
  - `Experimental` (compatible con la arquitectura pero no validada físicamente),
  - `Driver not yet supported` (tu versión de controlador aún no está validada — no se
    modifica nada),
  - `Multiple GPUs` (no se admite la selección automática de objetivo en esta versión
    preliminar),
  - `Not supported` (fuera de RTX 30 / Ampere SM86).
- Un pequeño botón **Technical details** muestra el modelo de GPU, la arquitectura, la
  capacidad de cómputo y la versión del controlador (sin datos internos).
- Las instalaciones silenciosas (`/VERYSILENT`) no se ven afectadas y nunca esperan en
  la página.

El motor del producto no cambió: la aplicación incluida es la misma compilación 0.4.2
validada. Esta versión es una mejora del instalador/UX.

## Novedades de la 0.4.2

- **Controles de la bandeja del sistema**: estado, juego actual, **Toggle Smooth Motion**
  con un clic, Abrir Administrador, Diagnósticos, Salir. Cierra el Administrador a la
  bandeja y sigue jugando.
- **Notificaciones nativas de Windows**: cuando alternas en vivo (bandeja, atajo de
  teclado o Administrador), aparece una notificación normal de Windows que muestra
  `Smooth Motion ON` / `Smooth Motion OFF` con el nombre del juego. Los casos de fallo
  también notifican (sin juego activo, en vivo no disponible, estado no verificado).
- La bandeja, el Administrador, el atajo de teclado y la CLI siguen siendo **un solo
  backend** (`runtime.toggle`); cada superficie lee el mismo estado verificado.
- Interruptor en vivo: **D3D11 validado instrumentalmente**; **D3D12 observado
  funcionando, con la instrumentación del motor activo actualmente no concluyente**
  (ver *Niveles de evidencia*). Las sesiones de Vulkan muestran "interruptor en vivo no
  disponible" (nunca se falsifica).

## Novedades de la 0.4.1

- **Control en vivo ON/OFF para un juego en ejecución.** Cuando un juego compatible está
  inyectado y en ejecución, el Administrador muestra una tarjeta **NOW PLAYING** con un
  botón ON/OFF de un clic que cambia el juego en ejecución de inmediato — sin terminal,
  sin reinicio. Ideal para una comparación A/B/A de la misma escena.
- **Atajo de teclado global opcional** (predeterminado **Ctrl + Alt + S**, configurable
  en los ajustes) para alternar en vivo sin salir del juego.
- El control en vivo usa el mismo motor de runtime validado que la CLI (`on`/`off`) y
  verifica el cambio con una lectura de retorno antes de informar éxito.
- Interruptor en vivo: **D3D11 validado instrumentalmente**; **D3D12 observado
  funcionando** (instrumentación del motor activo actualmente no concluyente). **No** se
  habilita para sesiones de Vulkan (se muestra como "no disponible para esta sesión").
- Empaquetado solo de distribución, administrador, biblioteca de juegos y detección de
  cambios de controlador como en la 0.4.0.

## Qué es esto

Una herramienta de vista previa de investigación sin firma que habilita NVIDIA Smooth
Motion en GPU Ampere SM86 (serie RTX 30), validada principalmente en una RTX 3090 con
controlador 616.64. Obtiene lo que necesita de tu propio controlador NVIDIA instalado;
no se redistribuye ningún binario de NVIDIA y el DriverStore nunca se modifica.

## Novedades de la 0.4.0

- **Administrador de Smooth Motion** con un interruptor maestro de un clic y un
  interruptor por juego.
- **Biblioteca de juegos** con escaneo (Steam, Epic, Game Pass) — elige un juego y pulsa
  Jugar.
- **Detección automática del sistema** con estado de compatibilidad en lenguaje sencillo.
- **Detección de cambios de controlador**: un perfil antiguo nunca se aplica a un
  controlador cambiado.
- **Empaquetado solo de distribución**: los datos del perfil de la versión están
  integrados en el producto compilado; no se incluye ningún archivo de receta legible.
- Licencia de usuario final propietaria (código fuente no publicado).

## Entorno validado

- NVIDIA RTX 3090 (SM86), un solo adaptador activo
- Controlador 616.64 (`32.0.16.1664`), Windows 10/11 x64

## Estado

- D3D11: títulos seleccionados, inicio directo del EXE — **validado
  instrumentalmente** (ON/OFF/ON en vivo en la configuración dorada).
- D3D12: títulos seleccionados — **observado funcionando**; la instrumentación del
  runtime del motor dinámico actualmente es **no concluyente** (no es una regresión).
- Compatible con la arquitectura (experimental): otras placas con una sola GPU RTX 30 /
  SM86 con el mismo controlador — misma arquitectura, no validadas físicamente.
- Experimental: Vulkan en Windows.
- No compatible: otras versiones de controlador, títulos de 32 bits, títulos con
  antitrampas.
- Multi-GPU: la vista previa para consumidores actual espera un único dispositivo
  objetivo CUDA/NVIDIA. La selección explícita de la GPU de renderizado está prevista
  para una versión posterior (una limitación de selección de dispositivo del
  administrador, no una incompatibilidad de hardware).

## Limitaciones conocidas

- Compilación sin firma (`UNSIGNED_RESEARCH_PREVIEW`).
- Los títulos de tiendas que se reinician en un nuevo proceso (Game Pass / algunos de
  Epic) aún no se siguen de forma fiable.
- Sin interruptor dentro del juego en la ruta de Vulkan.
- Se recomienda encarecidamente una FPS base más alta; una FPS base muy baja aumenta los
  artefactos y la latencia percibida.
