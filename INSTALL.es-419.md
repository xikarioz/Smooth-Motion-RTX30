[English](INSTALL.md) | [简体中文](INSTALL.zh-CN.md) | Español

# Instalación

## Requisitos

- Windows 10/11 x64 (64 bits)
- Arquitectura objetivo: **serie RTX 30 / Ampere SM86**
- Configuración dorada validada físicamente: **NVIDIA RTX 3090 + controlador 616.64**
  (`32.0.16.1664`), un único adaptador de pantalla activo
- Otras placas RTX 30 SM86 de una sola GPU: **experimentales** donde se acepta el
  controlador/perfil exacto — compatibles con la arquitectura, no validadas físicamente
- No se requieren permisos de administrador

La instalación **no** depende de una versión exacta del controlador: el instalador y el
Administrador también funcionan con controladores desconocidos. La activación de Smooth
Motion permanece **cerrada por seguridad** hasta que tu binario NvPresent instalado sea
reconocido y validado. Las GPU que no sean SM86 no son compatibles con el motor. Ver
[SUPPORT.es-419.md](SUPPORT.es-419.md) y
[COMPATIBILITY.es-419.md](COMPATIBILITY.es-419.md).

## Pasos

1. Descarga **`SmoothMotionSM86-Setup.exe`** desde el
   [última versión](https://github.com/xikarioz/Smooth-Motion-RTX30/releases/latest).
2. Verifica su SHA-256 contra `SHA256SUMS.txt` en la página de la versión.
3. Ejecuta el instalador. Primero realiza una comprobación de solo lectura de
   **System Compatibility** (compatibilidad del sistema) y muestra tu GPU, tu controlador
   NVIDIA, la arquitectura y un estado en lenguaje sencillo: `Compatible`,
   `Experimental`, `Driver not yet supported`, `Multiple GPUs` o `Not supported`.
4. Abre **Smooth Motion SM86** (menú Inicio o acceso directo del escritorio).
5. Activa **SMOOTH MOTION**.
6. Elige un juego de la biblioteca y pulsa **PLAY**.

Sin Python. Sin terminal. Windows SmartScreen puede mostrar un aviso porque esta versión
preliminar no está firmada; el SHA-256 es el ancla de integridad.

### Qué hace el administrador

- **Detección automática de GPU + controlador** con un estado de compatibilidad en
  lenguaje sencillo.
- **Interruptor maestro con un clic** e **interruptores por juego**.
- **Encendido/apagado en vivo** para un juego compatible en ejecución (botón del
  administrador, atajo de teclado global opcional o la bandeja del sistema) — A/B/A
  (misma escena) sin reiniciar.
- **Biblioteca de juegos** que escanea Steam, Epic y Game Pass.
- **De fallo seguro**: un controlador o diseño no reconocido se rechaza; no se modifica
  nada.

## Reparación, reversión y desinstalación

- **Reparación:** ejecuta el instalador de nuevo.
- **Reversión:** elimina las copias generadas del tiempo de ejecución (opción del
  administrador/bandeja del sistema, o `sm86.exe rollback`).
- **Desinstalación:** Configuración → Aplicaciones → *Smooth Motion SM86* (compilación
  instalada), o `Uninstall.cmd` (compilación portátil).

No se toca nada fuera de `%LOCALAPPDATA%\SmoothMotionSM86`. Tu controlador NVIDIA y tus
juegos nunca se modifican, y el DriverStore nunca se cambia.

## Instalación avanzada / portátil (heredada)

El `Setup.exe` de arriba es la ruta normal para el consumidor. También se publica una
compilación ZIP portátil para usuarios avanzados y máquinas sin conexión:

1. Descarga `SmoothMotionSM86-<version>-win64.zip` desde la página de la versión.
2. Verifica su SHA-256 contra `SHA256SUMS.txt`.
3. Extráelo donde quieras (por ejemplo, `%USERPROFILE%\Downloads\SmoothMotionSM86`).
4. Ejecuta `Instalar.cmd` — primero realiza una comprobación de compatibilidad de solo
   lectura, luego prepara el estado del tiempo de ejecución local a partir de tu propio
   controlador y crea el acceso directo del menú Inicio, o se detiene sin cambiar nada.
5. Abre **Smooth Motion SM86** desde el menú Inicio.

El ZIP portátil es el mismo tiempo de ejecución que el instalador; solo difieren la
entrega y el método de instalación.

### Línea de comandos (avanzada)

El `sm86.exe` incluido expone las mismas operaciones para usuarios avanzados:

```
sm86.exe doctor          # read-only GPU / active-driver / compatibility diagnosis
sm86.exe dashboard       # consumer-language system summary
sm86.exe prepare         # build the local runtime state from your installed driver
sm86.exe status | state  # requested / applied runtime state
sm86.exe on | off        # live toggle for the injected game
sm86.exe rollback        # remove project-owned generated artifacts
sm86.exe report          # privacy-reviewed diagnostic .zip (safe to attach to an issue)
```
