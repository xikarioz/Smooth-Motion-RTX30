[English](ROADMAP.md) | [简体中文](ROADMAP.zh-CN.md) | Español

# Hoja de ruta

Solo el alcance público. Las fechas no están prometidas.

## Completado (publicado)

- Producto Consumer Preview: administrador **Smooth Motion SM86**, `Setup.exe`,
  ON/OFF con un clic.
- **Biblioteca de juegos** que escanea Steam, Epic y Game Pass.
- Controles de la **bandeja del sistema** (estado, juego actual, interruptor, abrir el administrador, salir).
- **Atajo de teclado global opcional** (predeterminado **Ctrl + Alt + S**).
- **Interruptor ON/OFF en vivo** para un juego en ejecución — ruta en vivo D3D11
  validada instrumentalmente; D3D12 observado funcionando (ver [VALIDATION.md](VALIDATION.md)).
- **Notificaciones nativas de Windows** al alternar en vivo.
- **Página de compatibilidad del sistema del instalador** (GPU / controlador / arquitectura / estado).
- **Detección de cambios de controlador**: un perfil antiguo nunca se aplica a un controlador que cambió.

## Próximamente

- **Grabación de demostración ON → OFF → ON real** (metraje de juego sin modificar).
- **Más validación física de RTX 30** (informes de la comunidad → entradas revisadas).
- **Más perfiles de controlador NVIDIA** (solicita tu controlador; los perfiles se producen
  de forma privada y se entregan como actualizaciones de compatibilidad).
- **Inicio sin interrupciones en Game Pass / Epic** (seguimiento del renderizador final).
- **Productización de Vulkan** (sincronización de activación confiable).

## Más adelante

- Direccionamiento multi-GPU.
- Versiones firmadas (eliminar la fricción de SmartScreen).

## Fuera de esta hoja de ruta

Ingeniería inversa de componentes internos, investigación de kernel/FGX, o cualquier cosa
que exponga cómo se produce la compatibilidad. El proyecto entrega un producto; la
investigación permanece privada.
