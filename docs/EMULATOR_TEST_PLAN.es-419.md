[English](EMULATOR_TEST_PLAN.md) | [简体中文](EMULATOR_TEST_PLAN.zh-CN.md) | Español

# Plan de pruebas de emuladores

Estado: **NOT_TESTED.** Los emuladores se tratan como una clase de compatibilidad distinta. **No** se afirma compatibilidad con emuladores hasta que existan pruebas reales.

## Legal / alcance

- Prueba solo software **ya instalado y configurado legalmente por el usuario**.
- **No** proporciones, solicites ni ayudes a obtener firmware, claves, archivos BIOS ni adquisición de juegos protegidos por derechos de autor.
- Si hay un emulador de Switch presente y configurado legalmente en la propia máquina del probador, puede probarse como cualquier otro renderizador; de lo contrario, se omite.

## Conjunto inicial de emuladores

| Emulador | Estado |
|---|---|
| RPCS3 | `NOT_TESTED` |
| DuckStation | `NOT_TESTED` |
| PCSX2 | `NOT_TESTED` |
| Cemu | `NOT_TESTED` |
| Emuladores de Switch (si están instalados legalmente) | `NOT_TESTED` |
| Otros | `NOT_TESTED` |

## Preguntas por emulador

Para cada emulador, determina y registra:

1. **API de renderizado** — la que el emulador está configurado para usar.
2. **API de presentación real** — lo que realmente se presenta (puede diferir de la API de renderizado).
3. **Ruta de capas** — capas de traducción en la cadena, en orden.
4. **Conexión de NvPresent** — si se alcanza el backend de presentación del controlador.
5. **Estado de Smooth** — solicitado y aplicado.
6. **Observación de interpolación generada** — observación visual, explícitamente distinta de la prueba instrumentada del contenido.
7. **Comportamiento del ciclo de vida** — modelo de proceso, creación de dispositivo/swapchain, reinicios, recreación de la swapchain.
8. **FPS base** — valor real aproximado.
9. **Comportamiento de artefactos** — tipo, gravedad, condiciones.

## Formato del informe

```
Emulator:
Backend / API:
Game / workload:
Base FPS:
Smooth state (requested / applied):
Observed interpolation:
Artifacts:
Result:
```

## Reglas

- **No** reduzcas "el emulador arranca" a "Smooth Motion validado".
- Un emulador solo se informa aquí tras una prueba real y descrita en una configuración (GPU, controlador) descrita.
- No se añaden insignias ni afirmaciones de soporte especulativas sobre emuladores al README antes de que existan resultados reales.
