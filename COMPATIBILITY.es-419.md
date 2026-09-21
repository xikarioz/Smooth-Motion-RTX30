[English](COMPATIBILITY.md) | [简体中文](COMPATIBILITY.zh-CN.md) | Español

# Compatibilidad

Niveles usados por el proyecto. Un informe nunca promueve un nivel automáticamente; se revisa.

Tres dimensiones separadas (no las fusione):

- **Compatibilidad de hardware** — arquitectura objetivo (Ampere SM86 / serie RTX 30).
- **Validación física** — la tarjeta/controlador exactos realmente probados.
- **Soporte de producto multi-adaptador** — si el administrador puede seleccionar el
  dispositivo objetivo cuando hay más de una GPU.

| Nivel | Significado |
|---|---|
| **PROJECT_VALIDATED** | validado por el proyecto en la tarjeta de referencia |
| **COMMUNITY_CONFIRMED** | informe externo de alta calidad con diagnósticos adecuados |
| **COMMUNITY_REPORTED** | informe de usuario plausible, instrumentación incompleta |
| **EXPERIMENTAL** | compatible con la arquitectura, aún no validado |
| **UNTESTED** | sin datos todavía |
| **FAILED** | se reportó que no funciona |

Los resultados se registran por combinación de (GPU, controlador, juego, API, tienda, método de inicio);
el mismo juego puede diferir legítimamente entre entornos de inicio. Consulta
[COMMUNITY_VALIDATION.md](docs/COMMUNITY_VALIDATION.md).

## Windows

| GPU | Controlador | API | Estado |
|---|---|---|---|
| RTX 3090 | 616.64 | D3D11 | **PROJECT_VALIDATED** — ruta en vivo validada instrumentalmente |
| RTX 3090 | 616.64 | D3D12 | **PROJECT_VALIDATED (juego real)** — observado funcionando; la instrumentación en tiempo de ejecución del motor activo actualmente es no concluyente |
| RTX 3090 | 616.64 | Vulkan | PRACTICALLY_VALIDATED (ruta de investigación); inicio empaquetado EXPERIMENTAL |
| Otras RTX 30 / SM86 de una sola GPU (3080, 3070, 3060, 3050, portátil) | 616.64 | D3D11 / D3D12 | EXPERIMENTAL (compatible con la arquitectura; admitida cuando se acepta el controlador/perfil exacto) |
| Cualquier RTX 30 | otros controladores | — | UNTESTED (se rechaza hasta validarse) |
| Sistemas multi-GPU | 616.64 | — | Selección de dispositivo no implementada (ver abajo) |

## Selección de dispositivo

Sistemas multi-GPU: la Consumer Preview actual espera un único dispositivo objetivo
CUDA/NVIDIA. La selección explícita de la GPU de renderizado está prevista para una
versión posterior. Es una limitación de selección de dispositivo del administrador,
**no** evidencia de que esas GPU sean incompatibles.

## Linux (solo investigación — sin instalador)

| GPU | Controlador | Estado |
|---|---|---|
| RTX 3080 | 595.91.07 | RESEARCH_VALIDATED (transferencia externa; no productizado) |

## Informa tu resultado

Envía un
**[Informe de validación de hardware](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)**
con tu GPU, controlador, versión de Windows, juego, tienda, API y la observación
ON/OFF. Adjunta los diagnósticos exportados (**Exportar diagnósticos** en el
Administrador, o `sm86.exe report`). **No** subas DLL de NVIDIA ni volcados de
memoria. Los informes alimentan la tabla anterior tras su revisión, y un solo
informe nunca promueve una configuración a `PROJECT_VALIDATED`.
