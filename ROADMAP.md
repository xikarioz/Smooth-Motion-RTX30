English | [简体中文](ROADMAP.zh-CN.md) | [Español](ROADMAP.es-419.md)

# Roadmap

Public scope only. Dates are not promised.

## Completed (shipped)

- Consumer Preview product: **Smooth Motion SM86** manager, `Setup.exe`, one-click
  ON/OFF.
- **Game library** scanning Steam, Epic and Game Pass.
- **System tray** controls (status, current game, toggle, open Manager, exit).
- **Optional global hotkey** (default **Ctrl + Alt + S**).
- **Live ON/OFF toggle** for a running game — D3D11 instrumentally validated live
  path; D3D12 observed working (see [VALIDATION.md](VALIDATION.md)).
- **Native Windows notifications** on live toggle.
- **Installer System Compatibility page** (GPU / driver / architecture / status).
- **Driver-change detection**: an old profile is never applied to a changed driver.

## Next

- **Real ON → OFF → ON demo capture** (unmodified gameplay footage).
- **More RTX 30 physical validation** (community reports → reviewed entries).
- **More NVIDIA driver profiles** (request your driver; profiles are produced
  privately and delivered as compatibility updates).
- **Game Pass / Epic seamless launch** (final-renderer following).
- **Vulkan productization** (reliable activation timing).

## Later

- Multi-GPU targeting.
- Signed releases (remove SmartScreen friction).

## Not on this roadmap

Reverse-engineering internals, kernel/FGX research, or anything that would expose
how compatibility is produced. The project ships a product; the research stays
private.
