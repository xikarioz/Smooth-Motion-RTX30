[English](COMPATIBILITY.md) | 简体中文 | [Español](COMPATIBILITY.es-419.md)

# 兼容性

项目使用的层级。一份报告绝不会自动提升层级；它会被审核。

三个彼此独立的维度（不要将它们合并）：

- **硬件兼容性** — 目标架构（Ampere SM86 / RTX 30 系列）。
- **实机验证** — 实际测试过的确切显卡/驱动程序。
- **多适配器产品支持** — 当存在多个 GPU 时，管理器能否选择目标
  设备。

| 层级 | 含义 |
|---|---|
| **PROJECT_VALIDATED** | 由项目在参考显卡上验证 |
| **COMMUNITY_CONFIRMED** | 带有充分诊断信息的高质量外部报告 |
| **COMMUNITY_REPORTED** | 可信的用户报告，插桩不完整 |
| **EXPERIMENTAL** | 架构兼容，尚未验证 |
| **UNTESTED** | 暂无数据 |
| **FAILED** | 报告为不可用 |

结果按（GPU、驱动程序、游戏、API、商店前端、启动方式）组合记录；
同一个游戏在不同启动环境下可能合理地表现不同。请参阅
[COMMUNITY_VALIDATION.md](docs/COMMUNITY_VALIDATION.md)。

## Windows

| GPU | 驱动程序 | API | 状态 |
|---|---|---|---|
| RTX 3090 | 616.64 | D3D11 | **PROJECT_VALIDATED** — 仪器验证的实时路径 |
| RTX 3090 | 616.64 | D3D12 | **PROJECT_VALIDATED（真实游戏）** — 观察到可用；活动引擎运行时插桩目前尚无定论 |
| RTX 3090 | 616.64 | Vulkan | PRACTICALLY_VALIDATED（研究路径）；打包启动 EXPERIMENTAL |
| 其他单 GPU RTX 30 / SM86（3080、3070、3060、3050、笔记本） | 616.64 | D3D11 / D3D12 | EXPERIMENTAL（架构兼容；在确切的驱动程序/配置文件被接受时予以接纳） |
| 任意 RTX 30 | 其他驱动程序 | — | UNTESTED（在验证前拒绝） |
| 多 GPU 系统 | 616.64 | — | 设备选择未实现（见下文） |

## 设备选择

多 GPU 系统：当前消费者预览版期望单一的 CUDA/NVIDIA 目标
设备。显式的渲染 GPU 选择计划在后续版本中提供。这是
管理器设备选择方面的限制，**并非**那些 GPU 不兼容的
证据。

## Linux（仅研究 — 无安装程序）

| GPU | 驱动程序 | 状态 |
|---|---|---|
| RTX 3080 | 595.91.07 | RESEARCH_VALIDATED（外部移交；未产品化） |

## 报告你的结果

提交一份
**[硬件验证报告](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)**，
并附上你的 GPU、驱动程序、Windows 版本、游戏、商店前端、API 以及
ON/OFF 观察结果。附上导出的诊断信息（管理器中的**导出诊断信息**，
或 `sm86.exe report`）。**请勿**上传 NVIDIA DLL 或内存转储。报告经审核后
会汇入上表，且单份报告绝不会将某个配置提升为
`PROJECT_VALIDATED`。
