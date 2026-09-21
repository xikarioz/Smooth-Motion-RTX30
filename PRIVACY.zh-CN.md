[English](PRIVACY.md) | 简体中文 | [Español](PRIVACY.es-419.md)

# 隐私

Smooth Motion SM86 设计为完全离线工作。

## 本工具处理的数据

- GPU 型号与驱动程序版本（从 Windows 读取）。
- 你已安装的 `NvPresent64.dll` 的 SHA-256 哈希（用于验证兼容性）。
- 本工具准备内容的本地记录（`local-build.json`），以及
  `%LOCALAPPDATA%\SmoothMotionSM86` 下的本地操作日志。
- 实验性 Vulkan 路径在 `%TEMP%` 下的本地激活器日志。

## 网络

本应用不连接网络。没有遥测、没有分析、没有更新检查器，也没有账户系统。

## 你选择导出的诊断信息

`sm86.exe report`（或应用中的「导出诊断信息」）会创建一个本地 ZIP，其中包含：

- 工具版本、操作系统版本、GPU、驱动程序、哈希、所选配置文件；
- 诊断结果与高层运行时状态；
- 不包含任何 NVIDIA 二进制文件、内存转储或凭据；
- 个人路径改写为 `%USERPROFILE%`。

不会自动上传任何内容。是否将其附加到问题中由你决定。

## 移除

`Uninstall.cmd` 会移除项目自身的文件与快捷方式。除非传入 `-IncludeGenerated`，
否则生成的运行时副本会被保留（以便重装时复用）。本地日志可能作为操作的少量记录而保留；
删除 `%LOCALAPPDATA%\SmoothMotionSM86` 文件夹即可移除全部内容。

> 本译文仅为方便而提供。如措辞存在差异，以英文版本为准（英文版本是本项目的规范文档）。
