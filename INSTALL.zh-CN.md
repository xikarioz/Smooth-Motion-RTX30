[English](INSTALL.md) | 简体中文 | [Español](INSTALL.es-419.md)

# 安装

## 系统要求

- Windows 10/11 x64（64 位）
- 目标架构：**RTX 30 系列 / Ampere SM86**
- 经实机验证的黄金配置：**NVIDIA RTX 3090 + 驱动程序 616.64**
  （`32.0.16.1664`），单一活动显示适配器
- 其他单 GPU 的 SM86 RTX 30 显卡：在精确的驱动程序/配置文件被接受的情况下为
  **实验性** —— 架构兼容，但未经过实机验证
- 无需管理员权限

安装**不**绑定单一的驱动程序版本：安装程序和管理器在未知驱动程序上同样可以运行。
Smooth Motion 激活保持**故障关闭**，直到你安装的 NvPresent 二进制文件被识别并通过验证。
非 SM86 GPU 不受引擎支持。见
[SUPPORT.zh-CN.md](SUPPORT.zh-CN.md) 和 [COMPATIBILITY.zh-CN.md](COMPATIBILITY.zh-CN.md)。

## 步骤

1. 从[最新发行版](https://github.com/xikarioz/Smooth-Motion-RTX30/releases/latest)
   下载 **`SmoothMotionSM86-Setup.exe`**。
2. 将其 SHA-256 与发行页面上的 `SHA256SUMS.txt` 进行核对。
3. 运行安装程序。它首先执行只读的 **System Compatibility**（系统兼容性）检查，
   并显示你的 GPU、NVIDIA 驱动程序、架构以及一个通俗语言的状态：
   `Compatible`、`Experimental`、`Driver not yet supported`、`Multiple GPUs` 或
   `Not supported`。
4. 打开 **Smooth Motion SM86**（开始菜单或桌面快捷方式）。
5. 开启 **SMOOTH MOTION**。
6. 从游戏库中选择一个游戏，然后按 **PLAY**。

无需 Python。无需终端。Windows SmartScreen 可能会弹出提示，因为此预览版未签名 ——
SHA-256 才是完整性锚点。

### 管理器的作用

- **自动检测 GPU + 驱动程序**，并给出通俗语言的兼容性状态。
- **一键总开关**和**按游戏开关**。
- 对受支持的正在运行的游戏提供**实时开/关**（管理器按钮、可选的全局快捷键或系统
  托盘）—— 无需重启即可进行同场景 A/B/A。
- **游戏库**扫描 Steam、Epic 和 Game Pass。
- **故障关闭式**：未识别的驱动程序或布局会被拒绝；不会修改任何内容。

## 修复、回滚和卸载

- **修复：** 再次运行安装程序。
- **回滚：** 移除生成的运行时副本（管理器/托盘选项，或 `sm86.exe rollback`）。
- **卸载：** 设置 → 应用 → *Smooth Motion SM86*（已安装版本），或
  `Uninstall.cmd`（便携版本）。

不会触碰 `%LOCALAPPDATA%\SmoothMotionSM86` 之外的任何内容。你的 NVIDIA 驱动程序
与游戏永不被修改，DriverStore 也永不被更改。

## 高级 / 便携安装（旧版）

上面的 `Setup.exe` 是常规的消费者路径。同时还会为高级用户和离线机器发布便携式
ZIP 版本：

1. 从发行页面下载 `SmoothMotionSM86-<version>-win64.zip`。
2. 将其 SHA-256 与 `SHA256SUMS.txt` 进行核对。
3. 将其解压到任意位置（例如 `%USERPROFILE%\Downloads\SmoothMotionSM86`）。
4. 运行 `Instalar.cmd` —— 它首先运行一次只读的兼容性检查，然后根据你自己的
   驱动程序准备本地运行时状态并创建开始菜单快捷方式，或者停止而不更改任何内容。
5. 从开始菜单打开 **Smooth Motion SM86**。

便携式 ZIP 与安装程序是相同的运行时；只有交付和安装方式不同。

### 命令行（高级）

捆绑的 `sm86.exe` 为高级用户提供相同的操作：

```
sm86.exe doctor          # read-only GPU / active-driver / compatibility diagnosis
sm86.exe dashboard       # consumer-language system summary
sm86.exe prepare         # build the local runtime state from your installed driver
sm86.exe status | state  # requested / applied runtime state
sm86.exe on | off        # live toggle for the injected game
sm86.exe rollback        # remove project-owned generated artifacts
sm86.exe report          # privacy-reviewed diagnostic .zip (safe to attach to an issue)
```
