[English](VALIDATION.md) | [简体中文](VALIDATION.zh-CN.md) | Español

# Validación

El motor de compatibilidad de este proyecto es privado, por lo que este documento publica la **evidencia** en lugar del método. No contiene desplazamientos, direcciones, firmas, detalles internos del hook, detalles internos del clasificador ni binarios de NVIDIA, solo resultados de alto nivel y seguros para publicación.

Este es el **origen canónico** de la redacción de niveles de evidencia del proyecto. Otros documentos enlazan aquí en lugar de repetir afirmaciones matizadas.

## Sistema de referencia

| Elemento | Valor |
|---|---|
| GPU | NVIDIA GeForce RTX 3090 (GA102, Ampere SM86), único adaptador activo |
| Controlador | 616.64 (`32.0.16.1664`) |
| SO | Windows 10/11 x64 |
| API de gráficos | D3D11 y D3D12 nativos (producto empaquetado); Vulkan experimental |
| Instalar / preparar / revertir / desinstalar | Compatible |

Otras tarjetas SM86 RTX 30 de una sola GPU son compatibles con la arquitectura y son **experimentales** hasta su validación física. La compilación exacta reconocida de NvPresent **591.86** está **validada estáticamente / experimental** (aún no validada en vivo). Con compilaciones de NvPresent desconocidas o no validadas, el instalador y el Administrador siguen funcionando y la activación de Smooth Motion se rechaza (cerrada por seguridad, no se modifica nada).

## Adaptación de compatibilidad

En la compilación de referencia validada, la adaptación requerida es compacta y de alcance de metadatos:

- **41 sitios modificados / 61 bytes en total**
- 1 byte de elegibilidad de arquitectura del host
- 60 bytes de metadatos del módulo de GPU
- **20 objetivos de módulo no FP8 compatibles** adaptados
- **17 módulos dirigidos a FP8 excluidos deliberadamente** — Ampere SM86 carece de la ruta de ejecución nativa de Tensor Core FP8 a la que apuntan esos módulos
- **No se requirió ninguna reescritura de instrucciones SASS no FP8 probada** en la configuración de referencia validada

"Compacta" describe el resultado validado; no es una afirmación de minimalidad matemática. Aquí no se publican desplazamientos, firmas ni tablas de direcciones.

## Validación en tiempo de ejecución

La evidencia se recopiló a nivel de tiempo de ejecución y se describe solo en términos generales:

- **Observación real de módulos CUDA en tiempo de ejecución** — los módulos CUDA que realmente carga una sesión real se observan y se concilian con la población estática.
- **Paridad de transformación en sombra** — una derivación independiente se compara byte a byte con la compilación validada antes de conceder cualquier autoridad en tiempo de ejecución.
- **Validación activa del motor dinámico** — el motor controló sesiones reales y produjo las transformaciones esperadas con cero resultados CUDA distintos de cero.
- **Comprobaciones de reversión exactas** — cada activación es reversible, con lectura de retorno verificada para volver al estado original.
- **Controles ON/OFF/ON** — transiciones en vivo solicitado/aplicado seguidas a lo largo de fases mantenidas en la ruta D3D11.
- **Pruebas de ciclo de vida** — ciclos repetidos de conexión/inicialización sin autoridad filtrada y sin doble hook.

El motor de investigación actual también se ha validado en tiempo de ejecución frente a la configuración conocida como buena RTX 3090 / 616.64, incluida la paridad de transformación, la reversión transaccional y transiciones de estado en vivo repetidas.

## Resultado del motor de referencia

| Resultado | Valor |
|---|---|
| Transiciones de autoridad en vivo | **300** |
| Discrepancias de estado | **0** |
| Reversión | exacta |
| Ciclo de vida | aprobado |
| D3D11 A/B/A | aprobado |
| D3D12 | no concluyente — no se observó tráfico de carga de módulos en tiempo de ejecución durante la ventana de prueba; no se afirma como validado en tiempo de ejecución |

## Niveles de evidencia

El proyecto nunca confunde estos estados:

- *solicitado* ≠ *aplicado / activo* ≠ *backend en ejecución* ≠ *salida validada*
- "Observado funcionando" (observación directa del usuario en un juego real) no es "validado instrumentalmente" (evidencia automatizada del contenido de fotogramas).
- Una combinación validada (GPU, controlador, API, método de inicio, juego) no se generaliza a combinaciones no probadas.
- Niveles de la comunidad: `PROJECT_VALIDATED` · `COMMUNITY_CONFIRMED` · `EXPERIMENTAL` · `UNTESTED`. Un solo informe de usuario nunca promueve una configuración a `PROJECT_VALIDATED`.

Consulta [SUPPORT.es-419.md](SUPPORT.es-419.md), [COMPATIBILITY.es-419.md](COMPATIBILITY.es-419.md) y [RELEASE_NOTES.es-419.md](RELEASE_NOTES.es-419.md) para los niveles de producto.

## Lo que deliberadamente no se publica

La implementación del motor de compatibilidad es privada. Este documento omite intencionadamente la implementación del hook, direcciones, desplazamientos, firmas, detalles internos del clasificador y cualquier contenido binario sin procesar de NVIDIA. No se redistribuye ningún binario de NVIDIA.

> Esta traducción se ofrece por conveniencia. Si el texto difiere, la versión en inglés es el documento canónico del proyecto.
