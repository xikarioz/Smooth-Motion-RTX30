[English](SECURITY.md) | [简体中文](SECURITY.zh-CN.md) | Español

# Seguridad

## Uso previsto

Solo un jugador / sin conexión. **No** lo uses con títulos protegidos por antitrampas o
multijugador competitivo. La herramienta hace una heurística por nombre de archivo y
rechaza componentes antitrampa evidentes, pero ninguna heurística es una garantía.

## Qué hace la herramienta

- Lee tu controlador de NVIDIA instalado para verificar la GPU, la versión del controlador
  y el hash del binario.
- Prepara un estado de tiempo de ejecución adaptado en `%LOCALAPPDATA%\SmoothMotionSM86` a
  partir de tu propio controlador. Los archivos originales del controlador no se tocan.
- Carga el estado preparado en un proceso de juego al iniciar o (Vulkan experimental) adapta
  en memoria únicamente el backend firmado ya cargado.

## Qué no hace la herramienta

- Sin redistribución de binarios de NVIDIA.
- Sin modificación del DriverStore.
- No requiere derechos de administrador.
- Sin telemetría, sin acceso a la red, sin cuentas.
- Sin modificación de NVIDIA App ni de `nvdrsdb`.

## Comportamiento de fallo seguro

Controlador desconocido, hash desconocido, diseño inesperado, GPU no compatible o datos de
perfil ambiguos: la operación se detiene con un motivo claro y sin estado parcial. No existe
un modo de "mejor esfuerzo".

## Copia de seguridad y reversión

- Copias de la aplicación versionadas; sin sobrescribir una instalación en uso.
- `Uninstall.cmd` elimina solo archivos propios del proyecto (con protección de rutas).
- La reversión no toca tu controlador de NVIDIA — nunca se modificó.

## Diagnósticos

`sm86.exe report` produce un ZIP local solo con metadatos seguros. Nunca incluye binarios de
NVIDIA, volcados de memoria ni credenciales, y censura las rutas personales. Nada se sube
automáticamente.

## Informar de una vulnerabilidad

Informa de los problemas de seguridad de forma privada a través de los GitHub Security
Advisories del repositorio, no mediante un issue público. Incluye la versión, los pasos para
reproducirlo y si se modificó algún archivo del DriverStore o de un proveedor.

## Límites conocidos

- Compilación sin firmar; verifica el SHA-256 de la versión. SmartScreen puede avisar.
- El escaneo antitrampas es heurístico, no una garantía.
- No se confía en reempaquetados de terceros; descarga solo desde los Releases oficiales.

> Esta traducción se ofrece por conveniencia. Si el texto difiere, la versión en inglés es
> el documento canónico del proyecto.
