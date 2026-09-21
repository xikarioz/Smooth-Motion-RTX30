[English](PRIVACY.md) | [简体中文](PRIVACY.zh-CN.md) | Español

# Privacidad

Smooth Motion SM86 está diseñado para funcionar totalmente sin conexión.

## Datos que maneja la herramienta

- Modelo de GPU y versión del controlador (leídos de Windows).
- El hash SHA-256 de tu `NvPresent64.dll` instalado (para verificar la compatibilidad).
- Un registro local de lo que preparó la herramienta (`local-build.json`) y un diario
  local de acciones en `%LOCALAPPDATA%\SmoothMotionSM86`.
- Un registro local del activador en `%TEMP%` para la ruta Vulkan experimental.

## Red

La aplicación no se conecta a la red. No hay telemetría, ni analíticas, ni comprobador de
actualizaciones, ni sistema de cuentas.

## Diagnósticos que eliges exportar

`sm86.exe report` (o "Exportar Diagnósticos" de la aplicación) crea un ZIP local que contiene:

- versión de la herramienta, versión del SO, GPU, controlador, hashes, perfil seleccionado;
- diagnóstico y estado de tiempo de ejecución de alto nivel;
- sin binarios de NVIDIA, sin volcados de memoria, sin credenciales;
- rutas personales reescritas como `%USERPROFILE%`.

Nada se sube automáticamente. Tú decides si adjuntarlo a un issue.

## Eliminación

`Uninstall.cmd` elimina los archivos propios del proyecto y el acceso directo. Las copias de
tiempo de ejecución generadas se conservan salvo que se pase `-IncludeGenerated` (para que
una reinstalación pueda reutilizarlas). El diario local puede permanecer como un pequeño
registro de acciones; elimina la carpeta `%LOCALAPPDATA%\SmoothMotionSM86` para borrarlo todo.

> Esta traducción se ofrece por conveniencia. Si el texto difiere, la versión en inglés
> es el documento canónico del proyecto.
