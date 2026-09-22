[English](FAQ.md) | [简体中文](FAQ.zh-CN.md) | Español

# Preguntas frecuentes

**¿Necesito Python?**
No. El paquete de la versión es autónomo.

**¿Qué GPU/controlador necesito?**
Arquitectura objetivo: serie RTX 30 / Ampere **SM86**. La **RTX 3090 + controlador
616.64** está validada en vivo; la compilación exacta reconocida de NvPresent **591.86**
está **validada estáticamente / experimental**; otras placas RTX 30 SM86 de una sola GPU
son **experimentales** donde se reconoce el controlador/perfil exacto. Con un controlador
desconocido/no validado la app igualmente se instala y el Administrador se abre — la
activación de Smooth Motion permanece **cerrada por seguridad** hasta que tu binario
NvPresent sea reconocido y validado. Las GPU que no sean SM86 no son compatibles con el motor.

**Tengo dos GPU: ¿mi RTX 30 no es compatible?**
No. Sistemas con varias GPU: la actual versión preliminar para consumidores espera un
único dispositivo destino CUDA/NVIDIA; la selección explícita de la GPU de renderizado
está prevista para una versión posterior. Es una limitación de selección de dispositivo
del administrador, no una incompatibilidad de hardware.

**¿Modifica mi controlador?**
No. Lee tu controlador instalado y prepara un estado de tiempo de ejecución adaptado en
`%LOCALAPPDATA%`. El DriverStore nunca se modifica.

**¿Descarga algo?**
No. Funciona totalmente sin conexión. No hay telemetría.

**¿Es un mod de generación de fotogramas DLSS?**
No. Apunta a la ruta NvPresent / Smooth Motion a nivel de controlador de NVIDIA, no a
Streamline/NGX DLSS-G.

**¿D3D11 está validado igual que D3D12?**
No, y el proyecto los mantiene distintos. En la configuración dorada, **la ruta D3D11
encendido/apagado/encendido en vivo está validada instrumentalmente**. Los títulos
**D3D12** se han **observado funcionando en juegos reales**, pero la instrumentación
actual del motor dinámico activo en tiempo de ejecución es **no concluyente** (no se
observó tráfico de carga del módulo objetivo en la última ventana de validación; no se
clasifica como regresión). Ver `VALIDATION.md`.

**¿Puedo usarlo en juegos en línea/competitivos?**
No. Solo para un jugador/sin conexión. Los títulos protegidos por antitrampas quedan
fuera del alcance.

**¿Por qué veo artefactos o latencia adicional?**
Es interpolación temporal; la calidad depende de los FPS base. Con FPS base muy bajos
(alrededor de 20 FPS en nuestras pruebas), los artefactos y la latencia percibida
aumentan considerablemente. Se recomienda encarecidamente una mayor cantidad de FPS
base.

**El juego se inicia pero nada cambia.**
Asegúrate de haberlo iniciado a través de la aplicación, de que la generación de
fotogramas nativa esté desactivada, y revisa el **Estado**. Los juegos que se reinician
en un proceso nuevo pierden la activación por proceso.

**¿Cómo lo elimino?**
Compilación instalada: Configuración → Aplicaciones → *Smooth Motion SM86*. Compilación
portátil: `Uninstall.cmd` (opcionalmente `Uninstall.cmd -IncludeGenerated` para eliminar
también las copias generadas del tiempo de ejecución).

**¿Puedo redistribuirlo?**
No. Solo para uso personal; no se permite redistribuir ni reempaquetar. Ver `EULA.txt`.

**¿Cómo sé que la descarga es genuina?**
Verifica el SHA-256 en `SHA256SUMS.txt` contra la página de la versión. Descarga solo
desde los Releases del repositorio oficial.
