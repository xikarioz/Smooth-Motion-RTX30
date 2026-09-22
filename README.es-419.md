[English](README.md) | [简体中文](README.zh-CN.md) | Español

<p align="center">
  <img src="assets/banner.png" alt="Smooth Motion SM86" width="900">
</p>

# Smooth Motion SM86 — NVIDIA Smooth Motion para la serie RTX 30

**NVIDIA Smooth Motion en la serie RTX 30 / Ampere SM86. Un solo instalador. No se requiere integración de generación de fotogramas por juego.**

Smooth Motion SM86 habilita la ruta de interpolación de fotogramas **NvPresent / Smooth Motion** a nivel de controlador de NVIDIA en GPU Ampere SM86 donde NVIDIA actualmente no la expone — como una utilidad de Windows con un solo clic.

> **No es un mod de DLSS Frame Generation.**
> Usa la ruta Smooth Motion a nivel de presentación de NVIDIA en lugar de requerir la
> integración Streamline / DLSS-G de un juego.

**⬇ [Descargar v0.5.0-rc.1 para Windows — Vista previa de compatibilidad experimental (prelanzamiento)](https://github.com/xikarioz/Smooth-Motion-RTX30/releases/tag/v0.5.0-rc.1)**

> **Versión de prueba actual: v0.5.0-rc.1 (prelanzamiento).** Incluye la corrección del fallo de inicio del Administrador, la corrección de los campos dinámicos del instalador en chino simplificado y una ruta **validada estáticamente** experimental para la compilación exacta reconocida de NvPresent **591.86**. **616.64 sigue siendo la configuración dorada validada en vivo.** 591.86 *no* está validada en vivo todavía: pruébala y cuéntanoslo.
>
> La insignia/etiqueta "latest" de GitHub sigue apuntando a la última versión **estable**; el prelanzamiento anterior es la compilación de prueba actual.

RTX 30 / SM86 · D3D11 · D3D12 · Vulkan experimental · Windows 10/11 x64

![Prelanzamiento actual](https://img.shields.io/badge/prerelease-v0.5.0--rc.1-orange)
![Plataforma](https://img.shields.io/badge/platform-Windows-0078D6)
![GPU](https://img.shields.io/badge/GPU-RTX%2030%20%2F%20SM86-76B900)
![Estado](https://img.shields.io/badge/status-Consumer%20Preview-orange)

Arquitectura objetivo: **serie RTX 30 / Ampere SM86.** La **RTX 3090 + controlador
616.64** está validada en vivo; la compilación exacta reconocida de NvPresent
**591.86** está **validada estáticamente / experimental**. Un controlador no
reconocido no significa “no se puede instalar”: el instalador y el Administrador
siguen funcionando, con Smooth Motion **cerrado por seguridad** hasta que el binario
NvPresent instalado sea reconocido y validado.

**Probado en 16 juegos reales, en múltiples motores y entornos de lanzamiento — incluidos títulos D3D11, D3D12 y de Game Pass.**

---

## Míralo en acción

**Próximamente: captura real de la misma escena ON → OFF → ON.**

La demostración usará metraje de juego sin modificar, sin interpolación sintética y sin manipulación de la velocidad de reproducción.

## Probado en juegos reales

| Juego | Estado de prueba |
|---|---|
| Assassin's Creed Origins | ✅ Smooth Motion observado funcionando |
| Assassin's Creed Odyssey | ✅ Validación en tiempo de ejecución / en vivo ON → OFF → ON |
| Black Myth: Wukong | ✅ Smooth Motion observado funcionando |
| Resident Evil 4 | ✅ Smooth Motion observado funcionando |
| Resident Evil Requiem | ✅ Smooth Motion observado funcionando |
| Alan Wake 2 | ✅ Smooth Motion observado funcionando |
| Cyberpunk 2077 | ✅ Smooth Motion observado funcionando |
| The Last of Us | ✅ Smooth Motion observado funcionando |
| Hogwarts Legacy | ✅ Smooth Motion observado funcionando / carga de trabajo de medición |
| Clair Obscur: Expedition 33 — Game Pass | ✅ Smooth Motion observado funcionando |
| Marvel's Spider-Man 2 | ✅ Smooth Motion observado funcionando |
| Hades | ✅ Smooth Motion observado funcionando |
| Until Dawn | ✅ Smooth Motion observado funcionando |
| Kingdom Come: Deliverance II | ✅ Smooth Motion observado funcionando |
| Persona 3 Reload | ✅ Smooth Motion observado funcionando |
| Pragmata | ✅ Smooth Motion observado funcionando |

> **Nota de evidencia:** “observado funcionando” significa que Smooth Motion se habilitó y su efecto se observó directamente durante el juego real. No implica que todos los títulos recibieran el mismo nivel de instrumentación o una validación independiente del contenido de los fotogramas.

## Inicio rápido

1. Descarga **`SmoothMotionSM86-Setup.exe`** desde el [prelanzamiento v0.5.0-rc.1](https://github.com/xikarioz/Smooth-Motion-RTX30/releases/tag/v0.5.0-rc.1).
2. Ejecútalo (sin derechos de administrador, sin Python, sin terminal).
3. Abre **Smooth Motion SM86**.
4. Activa **SMOOTH MOTION**.
5. Elige un juego y pulsa **JUGAR**.

Guía completa: [INSTALL.es-419.md](INSTALL.es-419.md) · Problemas: [TROUBLESHOOTING.es-419.md](TROUBLESHOOTING.es-419.md)

## Qué obtienes

Un administrador pensado para jugadores que hace por ti la parte difícil:

- **Detección automática de GPU y controlador** con un estado de compatibilidad en lenguaje claro.
- **Interruptor maestro con un clic** e **interruptores por juego**.
- **Encendido/apagado en vivo** para un juego compatible en ejecución — cámbialo en pleno juego (botón del Administrador, el atajo global opcional o la **bandeja del sistema**) para una comparación A/B/A en la misma escena, sin reiniciar. Los resultados aparecen como una notificación normal de Windows.
- Controles en la **bandeja del sistema** (estado, juego actual, alternar, abrir el Administrador, salir); el Administrador se puede cerrar a la bandeja.
- **Biblioteca de juegos** que escanea Steam, Epic y Game Pass — elige un juego y pulsa Jugar.
- **De fallo seguro**: si no se reconoce el binario de tu controlador, no se modifica nada.
- **Reversible**: la reversión y la desinstalación están integradas. Nunca se toca el DriverStore y no se redistribuye ningún binario de NVIDIA.

## ¿En qué se diferencia de los mods de DLSS-G?

Neutro, una línea cada uno:

- **Smooth Motion SM86**: juego → ruta de presentación de NVIDIA → **NvPresent / Smooth Motion** → fotogramas generados.
- **Mods de DLSS Frame Generation**: juego con integración DLSS-FG → Streamline / NGX → **DLSS-G** → fotogramas generados.

Distinta capa de integración, distinto punto de adaptación. Este proyecto trabaja con el backend de presentación del controlador, no con la integración DLSS-FG del juego.

## Compatibilidad

**Política actual (v0.5.0-rc.1 y posteriores): la versión del controlador por sí sola
ya no decide si la aplicación puede instalarse.** El instalador y el Administrador
funcionan con controladores desconocidos; la activación de Smooth Motion permanece
**cerrada por seguridad** hasta que el binario NvPresent instalado sea reconocido y
validado.

| Configuración | Estado | Administrador | Smooth Motion |
|---|---|---|---|
| RTX 3090 + controlador 616.64 (dorada) | **Validada en vivo** | Sí | Sí |
| Compilación exacta reconocida de NvPresent 591.86 | **Validada estáticamente / experimental** | Sí | Experimental (aún no validada en vivo) |
| NvPresent desconocido / no validado | No validado | Sí | No — cerrado por seguridad |
| GPU no SM86 (RTX 40/50, RTX 20, GTX 10, AMD/Intel) | No compatible con el motor | Sí | No |
| Sistemas multi-GPU | Selección de dispositivo no implementada | Sí | No |

Tres dimensiones separadas, mantenidas distintas a propósito:

- **Compatibilidad de hardware:** Ampere **SM86 / serie RTX 30** es la arquitectura objetivo.
- **Validación física/en vivo:** solo la **RTX 3090 + controlador 616.64** está validada físicamente.
- **Otras tarjetas RTX 30 SM86 de una sola GPU** son **experimentales** una vez reconocido el controlador/perfil exacto (no “no compatibles”).
- **D3D11** ruta en vivo del motor dinámico: **validada instrumentalmente**. **D3D12**: observada funcionando en juegos reales (instrumentación del motor activo actualmente no concluyente).
- **Títulos de 32 bits y protegidos por antitrampas** no son compatibles.

> Nota histórica: las versiones v0.4.x estaban restringidas al perfil validado 616.64. Esa restricción se eliminó en v0.5.0-rc.1; consulta las notas de la versión.

Detalles y niveles: [SUPPORT.es-419.md](SUPPORT.es-419.md) · [COMPATIBILITY.es-419.md](COMPATIBILITY.es-419.md) · [VALIDATION.es-419.md](VALIDATION.es-419.md)

## Validación

El motor de compatibilidad es propietario, por lo que la evidencia se documenta públicamente en su lugar. **[VALIDATION.es-419.md](VALIDATION.es-419.md)** cubre el sistema dorado, la adaptación compacta, la validación en tiempo de ejecución y los niveles de evidencia del proyecto.

Resumen: en la compilación dorada validada **RTX 3090 / controlador 616.64**, la adaptación es de **41 sitios modificados / 61 bytes en total** — 20 objetivos de módulos no FP8 compatibles adaptados, **17 módulos dirigidos a FP8 excluidos deliberadamente**, y no se requirió reescribir ninguna instrucción SASS no FP8 probada. El motor de investigación actual reproduce esa configuración dorada en tiempo de ejecución, incluida la paridad de transformación, la reversión transaccional y repetidas transiciones de estado en vivo (300 transiciones, 0 discrepancias de estado).

- **D3D11** — la ruta en vivo ON/OFF/ON está **validada instrumentalmente** en la configuración dorada.
- **D3D12** — Smooth Motion se **observa funcionando en juegos D3D12 reales**, pero la instrumentación en tiempo de ejecución del motor dinámico activo actual es **no concluyente** (no se observó tráfico de carga de módulos objetivo en la ventana de validación más reciente del motor activo). Esto no se clasifica como una regresión.

## Seguridad y confianza

- **Sin redistribución de binarios de NVIDIA** — deriva lo que necesita de tu propio controlador instalado.
- **DriverStore intacto** — los archivos originales del controlador nunca se modifican.
- **De fallo seguro** — controlador/diseño desconocido → sin parche, y se te dice por qué.
- **Reversible** — instalación por versión, reversión, desinstalación.
- **Privacidad** — sin conexión, sin telemetría, sin cuentas; ver [PRIVACY.es-419.md](PRIVACY.es-419.md).
- **Sumas de verificación publicadas** — verifica la descarga con `SHA256SUMS.txt`.
- **Vista previa para consumidores sin firmar** — SmartScreen puede avisar; el SHA-256 es el ancla de integridad.

## Limitaciones conocidas

- Vista previa para consumidores sin firmar — SmartScreen puede avisar; verifica el SHA-256.
- Los títulos de tiendas que se relanzan en un proceso nuevo (algunos de Game Pass / Epic) aún no se siguen de forma fiable.
- Vulkan en Windows es experimental; no hay interruptor dentro del juego.
- **Sistemas multi-GPU: la Vista previa para consumidores actual espera un único dispositivo objetivo CUDA/NVIDIA. La selección explícita de la GPU de renderizado está prevista para una versión posterior.** Es una limitación de selección de dispositivo del administrador, **no** una incompatibilidad de hardware.
- Se recomienda encarecidamente una FPS base más alta; una FPS base muy baja aumenta los artefactos y la latencia percibida.

## Capturas de pantalla

El **Administrador de Smooth Motion SM86** real en el sistema validado (RTX 3090 + controlador 616.64): detección automática de GPU/controlador, estado de compatibilidad, el interruptor maestro y el control **EN JUEGO** en vivo.

![Administrador de Smooth Motion SM86](assets/manager-top.png)

El **instalador** detecta tu GPU, el controlador de NVIDIA y la compatibilidad antes de instalar nada:

![Página de compatibilidad del instalador de Smooth Motion SM86](assets/setup-compat.png)

*Una ejecución real de Setup v0.4.3 en la RTX 3090 + controlador 616.64 validada.*

## Hoja de ruta

Más validación física de RTX 30 · más perfiles de controlador · inicio fluido en Game Pass / Epic · productización de Vulkan · selección multi-GPU · versiones firmadas. Ver [ROADMAP.es-419.md](ROADMAP.es-419.md).

## Ayuda a validar más GPU RTX 30

¿Tienes una **RTX 3050 / 3060 / 3060 Ti / 3070 / 3070 Ti / 3080 / 3080 Ti** (u otra tarjeta SM86 de una sola GPU)? La validación comunitaria en sistemas Ampere SM86 adicionales es especialmente útil.

Si Smooth Motion funciona en tu sistema, envía el **[Informe de validación de hardware](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)** estructurado con:

- Modelo de GPU (+ ID de PCI si los diagnósticos lo muestran) y versión del controlador
- Versión de Windows
- juego (y compilación si es práctico)
- tienda y método de lanzamiento (el mismo juego puede diferir según el entorno de lanzamiento)
- API de gráficos si se conoce
- **FPS base** aproximada, resolución y frecuencia de actualización
- estado solicitado (requested) frente a aplicado (applied) de Smooth Motion, y la interpolación observada
- gravedad de fallos / artefactos
- los diagnósticos exportados (**Exportar diagnósticos** en el Administrador, o `sm86.exe report`)
- si probaste un alternado en vivo, y lo que viste

Los debates y resultados están en **Discussions**; usa **Issues** para errores reproducibles del producto. Esquema completo y el modelo de niveles de evidencia: [docs/COMMUNITY_VALIDATION.es-419.md](docs/COMMUNITY_VALIDATION.es-419.md).

Los informes nunca promueven una configuración a `PROJECT_VALIDATED` por sí solos. Consulta el modelo de niveles en [COMPATIBILITY.es-419.md](COMPATIBILITY.es-419.md): `PROJECT_VALIDATED` (proyecto, tarjeta de referencia) · `COMMUNITY_CONFIRMED` (informe externo de alta calidad) · `COMMUNITY_REPORTED` (instrumentación plausible pero incompleta) · `EXPERIMENTAL` (compatible con la arquitectura, aún no validada) · `UNTESTED`.

Si el proyecto te resultó útil, considera **darle una estrella**.

## Licencia

Propietaria, código fuente no publicado. Se permite el uso personal; sin redistribución ni reempaquetado. Ver [EULA.es-419.txt](EULA.es-419.txt).

NVIDIA Smooth Motion, NvPresent y CUDA son tecnologías de NVIDIA, no incluidas aquí. Este es un proyecto independiente, no afiliado ni respaldado por NVIDIA.
