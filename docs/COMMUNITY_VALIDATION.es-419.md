[English](COMMUNITY_VALIDATION.md) | [简体中文](COMMUNITY_VALIDATION.zh-CN.md) | Español

# Validación de la comunidad

Smooth Motion SM86 se valida principalmente en una única configuración de referencia (RTX 3090 + controlador 616.64). La confianza más amplia proviene de informes estructurados de la comunidad. Este documento explica cómo enviar uno, cómo se clasifican los resultados y por qué el modelo es deliberadamente multidimensional.

Un informe nunca promueve por sí solo una configuración a `PROJECT_VALIDATED`.

## Dónde publicar

- **Issues** — errores reproducibles del producto.
- **Discussions** — resultados, conversación sobre compatibilidad y temas de investigación. Categorías recomendadas:
  - **Hardware Validation** — envía y comenta [informes de validación de hardware](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml).
  - **Game Compatibility** — comportamiento por título y por tienda.
  - **Research / Technical Discussion** — rutas de API, comportamiento del ciclo de vida, metodología.
  - **Installation / Setup Help** (opcional) — poner todo en marcha.

> La configuración de categorías puede requerir un paso manual único en **Settings → Features → Discussions** si las categorías anteriores aún no existen.

## Enviar un informe

Usa la plantilla de **[informe de validación de hardware](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)**. Exporta los diagnósticos desde el Administrador (**Export Diagnostics**) o ejecuta `sm86.exe report`, y luego adjunta el resultado. Nunca adjuntes DLL de NVIDIA, volcados de memoria ni rutas personales.

## Por qué importan las dimensiones

"El juego X funciona" no equivale a "el juego X funciona en todos los entornos de inicio". El mismo título puede comportarse de forma distinta según la tienda, el método de inicio y la tasa de fotogramas base. Por eso cada resultado se registra como una combinación:

| Dimensión | Por qué se registra |
|---|---|
| GPU + controlador | La compatibilidad es una propiedad del par (GPU, controlador) |
| Tienda | Steam / Epic / Game Pass / GOG / independiente / emulador se inician de forma distinta |
| Método de inicio | El proceso del lanzador, el EXE directo, el proceso hijo, la reejecución y los envoltorios de tienda cambian el momento de conexión |
| API de gráficos | D3D11 / D3D12 / Vulkan / rutas traducidas tienen ciclos de vida distintos |
| FPS base | La calidad de interpolación y la gravedad de los artefactos dependen en gran medida del espaciado temporal |
| Resolución + frecuencia | Contexto de presentación |
| Estado solicitado vs aplicado | `requested ≠ applied`; no deben fusionarse |
| Interpolación observada | La observación visual no es prueba instrumentada del contenido |
| Fallo / artefactos | Señal de estabilidad y calidad |
| Diagnósticos | Reproducibilidad y clasificación |

No se afirma un umbral universal de FPS base; el valor real se registra para que el análisis futuro pueda estudiar la gravedad de los artefactos, la latencia y el comportamiento del backend frente a los FPS base.

## Niveles de evidencia

Cada combinación (GPU, controlador, juego, API, tienda, método de inicio) se asigna a un nivel:

| Nivel | Significado |
|---|---|
| `PROJECT_VALIDATED` | instrumentado / reproducido por el equipo del proyecto en la configuración de referencia |
| `COMMUNITY_CONFIRMED` | informe externo de alta calidad con diagnósticos adecuados |
| `COMMUNITY_REPORTED` | informe de usuario plausible, instrumentación incompleta |
| `EXPERIMENTAL` | arquitectura / ruta admitida pero no suficientemente probada |
| `UNTESTED` | sin evidencia |

Los mantenedores asignan el nivel tras la revisión. Un resultado anecdótico único nunca se promueve a `PROJECT_VALIDATED`.

## Esquema de observación de compatibilidad (seguro para publicación)

Esta es la forma de registro segura para publicación que se usa para estructurar los resultados. No contiene detalles internos de ingeniería inversa.

```json
{
  "gpu": "RTX 3080",
  "gpu_arch": "Ampere SM86",
  "driver": "616.64",
  "windows": "Windows 11 23H2",
  "game": "Example Game",
  "game_build": "1.0",
  "api": "D3D12",
  "storefront": "Steam",
  "launch_method": "Direct EXE",
  "base_fps": 55,
  "resolution": "2560x1440",
  "refresh_hz": 144,
  "requested_state": true,
  "applied_state": true,
  "interpolation_observed": "yes",
  "crash": false,
  "artifacts": "NONE",
  "diagnostics": "attached",
  "evidence_tier": "COMMUNITY_REPORTED",
  "reporter": "github-handle",
  "date": "2026-09-20"
}
```

Una fila es una combinación. El mismo juego puede aparecer varias veces con distintas tiendas, métodos de inicio o resultados; eso es esperado, no una contradicción.

## Tabla de compatibilidad de la comunidad (estructura)

Los resultados probados por el proyecto y los informes de la comunidad se mantienen separados. Con el tiempo se añaden nuevas filas verificadas; nada se promueve automáticamente desde este documento.

| GPU | Controlador | Juego | Tienda | Inicio | FPS base | Resultado | Nivel de evidencia |
|---|---|---|---|---|---|---|---|
| RTX 3090 | 616.64 | Cyberpunk 2077 | Steam | Direct EXE | — | Observado funcionando | `PROJECT_VALIDATED` |

La matriz poblada del proyecto está en el [README](../README.es-419.md#tested-in-real-games).

## Emuladores

Los emuladores se tratan como una clase de compatibilidad distinta y **no** se afirma que funcionen. Consulta [EMULATOR_TEST_PLAN.es-419.md](EMULATOR_TEST_PLAN.es-419.md); el estado actual de todos los emuladores probados es `NOT_TESTED`.
