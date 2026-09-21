[English](SUPPORT.md) | [简体中文](SUPPORT.zh-CN.md) | Español

# Estado de soporte

Smooth Motion SM86 admite una configuración deliberadamente estrecha y validada. Otras
combinaciones se rechazan en lugar de adivinarse.

Se rastrean tres dimensiones separadas (no las fusione):

- **Compatibilidad de hardware** — la arquitectura de GPU a la que el motor puede apuntar (Ampere SM86).
- **Validación física** — la combinación exacta de tarjeta/controlador realmente probada.
- **Soporte de producto multi-adaptador** — si el administrador actual puede *seleccionar*
  el dispositivo objetivo correcto cuando hay más de una GPU.

## Configuración de referencia (probada físicamente)

| Elemento | Estado |
|---|---|
| GPU | NVIDIA RTX 3090 (GA102, Ampere SM86), un único adaptador activo |
| Controlador | 616.64 (`32.0.16.1664`) |
| SO | Windows 10/11 x64 |
| Ruta en vivo D3D11 | **Validado instrumentalmente** — ON/OFF/ON en vivo sobre la configuración de referencia |
| Ruta de juego real D3D12 | **Observado funcionando** — la instrumentación en tiempo de ejecución del motor dinámico activo actualmente es **no concluyente** |
| Instalar / preparar / revertir / desinstalar | Compatible |

## Experimental

| Elemento | Notas |
|---|---|
| Otras tarjetas Ampere SM86 RTX 30 de una sola GPU (RTX 3080 / 3080 Ti / 3070 / 3060 / 3050, portátil incluida) con controlador 616.64 | Misma arquitectura; **admitida técnicamente cuando se acepta el controlador/perfil exacto**, no validada físicamente. Puede funcionar; sin promesa. |
| Windows Vulkan | Ruta de investigación demostrada; la activación empaquetada es experimental y puede no sobrevivir a los reinicios del proceso del cliente de tienda. |
| Conmutación dentro del juego en la ruta Vulkan | No implementada. |

## No compatible

- Otras versiones de controlador (rechazadas; sin adivinar).
- GPU que no son SM86 (RTX 40/50, RTX 20, GTX 10, AMD/Intel).
- Títulos de 32 bits.
- Títulos con protección antitrampas o multijugador competitivo.
- Actualizaciones automáticas (ninguna; descarga las versiones nuevas manualmente).

## Selección de dispositivo (no es una limitación de hardware)

Sistemas multi-GPU: la Consumer Preview actual espera un único dispositivo objetivo
CUDA/NVIDIA. La selección explícita de GPU de renderizado se prevé para una versión posterior.

Es una **limitación de selección de dispositivo del administrador**, no evidencia de que
esas GPU sean incompatibles. La admisión de arquitectura del motor es independiente de
cuántos adaptadores haya instalados.

## Cómo se decide la compatibilidad

La herramienta verifica, en orden: un perfil revisado para el binario NvPresent de tu
controlador, el hash exacto del binario, la versión exacta del controlador de Windows,
exactamente un dispositivo CUDA y la capacidad de cómputo exacta SM86. Cualquier
discrepancia detiene el proceso con un motivo claro.

## Niveles de la comunidad

| Nivel | Significado |
|---|---|
| `PROJECT_VALIDATED` | validado por el proyecto en la tarjeta de referencia |
| `COMMUNITY_CONFIRMED` | varios informes de usuarios independientes con evidencia plausible |
| `COMMUNITY_REPORTED` | informe de usuario plausible, instrumentación incompleta |
| `EXPERIMENTAL` | compatible con la arquitectura, aún no validado |
| `UNTESTED` | sin datos todavía |

Un solo informe de usuario nunca promueve una configuración a `PROJECT_VALIDATED`. Consulta
[COMMUNITY_VALIDATION.md](docs/COMMUNITY_VALIDATION.md) para el esquema del informe y
las dimensiones de tienda / método de inicio / FPS base.

## Informar resultados

Envía un
**[Informe de validación de hardware](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)**
con GPU, controlador, versión de Windows, juego, tienda, API de gráficos y los
diagnósticos exportados (**Exportar diagnósticos** en el Administrador, o `sm86.exe report`).
Los informes nunca promueven por sí solos una configuración a "validada".
