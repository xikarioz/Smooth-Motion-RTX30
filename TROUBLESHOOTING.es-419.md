[English](TROUBLESHOOTING.md) | [简体中文](TROUBLESHOOTING.zh-CN.md) | Español

# Solución de problemas

## La comprobación de compatibilidad dice que mi GPU/controlador no es compatible

La herramienta rechaza en lugar de adivinar. Solo valida físicamente una tarjeta
(RTX 3090) con el controlador 616.64; otras versiones de controlador y GPU que no son
SM86 se rechazan. Si tienes una sola GPU RTX 30 / SM86 con el controlador validado, se
admite como **experimental** cuando se acepta el controlador/perfil exacto (no "no compatible").

## Tengo dos GPU (multi-GPU)

La Consumer Preview actual espera un único dispositivo objetivo CUDA/NVIDIA. La selección
explícita de GPU de renderizado está prevista para una versión posterior. Es una
**limitación de selección de dispositivo del administrador, no una incompatibilidad de
hardware** — la arquitectura objetivo (Ampere SM86 / serie RTX 30) no se ve afectada por
cuántos adaptadores estén instalados.

## El juego se inicia pero no noto diferencia

1. Revisa **Estado** — `null` significa DESCONOCIDO, nunca False.
2. Desactiva la generación de fotogramas **nativa** del juego en su menú; no acumules
   otros mods de generación de fotogramas.
3. Asegúrate de que el juego se inició mediante **Iniciar juego** de la aplicación (o
   `sm86.exe launch`). La inyección es por proceso; un juego que se relanza en un proceso
   nuevo la pierde — el seguimiento automático no está habilitado.
4. Usa el modo sin bordes/ventana para medir; el contador de FPS del juego más la
   superposición de NVIDIA es la lectura recomendada.

## Muchos artefactos o latencia alta

En nuestras pruebas, con una FPS base muy baja — alrededor de 20 FPS — los artefactos de
interpolación y la latencia percibida aumentaron de forma notable. Sube la FPS base antes
de activar Smooth. No esperes que Smooth haga que 20 FPS se sientan como 40 FPS con calidad perfecta.

## Juegos con Vulkan en Windows

La ruta Vulkan es experimental. Algunos títulos de tiendas (p. ej. Game Pass) se relanzan
en un proceso de juego nuevo, lo que anula la activación por proceso; esos aún no son
compatibles. Ver [SUPPORT.md](SUPPORT.es-419.md).

## "Controlador desconocido" / no se modifica nada

Correcto: los controladores desconocidos se rechazan, no se modifican. La herramienta
nunca adivina.

## Eliminación limpia

- `Uninstall.cmd` — elimina los archivos de la aplicación + el acceso directo (conserva
  las copias de tiempo de ejecución generadas).
- `Uninstall.cmd -IncludeGenerated` — también elimina las copias generadas.
- `sm86.exe rollback` — elimina solo las copias generadas.

El desinstalador rechaza cualquier ruta fuera de `%LOCALAPPDATA%\SmoothMotionSM86`.

## Informar de un problema

Exporta Diagnósticos desde la aplicación (o ejecuta `sm86.exe report`). Crea un ZIP solo
con metadatos seguros — diagnóstico, hashes, perfil, estado de alto nivel — con las rutas
personales censuradas. No contiene binarios de NVIDIA. Revísalo antes de adjuntarlo.
Incluye GPU, controlador, versión de Windows, juego, API y si se desactivó la FG nativa.
