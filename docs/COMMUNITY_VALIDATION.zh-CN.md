[English](COMMUNITY_VALIDATION.md) | 简体中文 | [Español](COMMUNITY_VALIDATION.es-419.md)

# 社区验证

Smooth Motion SM86 主要在一个黄金配置（RTX 3090 + 驱动程序 616.64）上验证。更广泛的信心来自结构化的社区报告。本文档说明如何提交报告、结果如何分类，以及为什么该模型刻意保持多维。

报告本身绝不会将某个配置提升为 `PROJECT_VALIDATED`。

## 发布位置

- **Issues**——可复现的产品缺陷。
- **Discussions**——结果、兼容性讨论和研究主题。推荐类别：
  - **Hardware Validation**——提交并讨论 [硬件验证报告](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)。
  - **Game Compatibility**——逐游戏和逐商店的行为。
  - **Research / Technical Discussion**——API 路径、生命周期行为、方法论。
  - **Installation / Setup Help**（可选）——让程序运行起来。

> 如果上述类别尚不存在，类别设置可能需要在 **Settings → Features → Discussions** 中进行一次性手动操作。

## 提交报告

使用 **[硬件验证报告](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)** 模板。从管理器导出诊断信息（**Export Diagnostics**），或运行 `sm86.exe report`，然后附上结果。切勿附上 NVIDIA DLL、内存转储或个人路径。

## 为什么这些维度很重要

「游戏 X 可用」并不等同于「游戏 X 在所有启动环境下都可用」。同一款游戏在不同商店、启动方式和基础帧率下表现可能不同。因此每个结果都记录为一个组合：

| 维度 | 为何记录 |
|---|---|
| GPU + 驱动程序 | 兼容性是（GPU、驱动程序）对的属性 |
| 商店 | Steam / Epic / Game Pass / GOG / 独立 / 模拟器的启动方式各不相同 |
| 启动方式 | 启动器进程、直接 EXE、子进程、重新执行和商店包装器会改变附加时机 |
| 图形 API | D3D11 / D3D12 / Vulkan / 转换路径具有不同的生命周期 |
| 基础 FPS | 插值质量和伪影严重程度在很大程度上取决于时间间隔 |
| 分辨率 + 刷新率 | 呈现上下文 |
| 已请求 vs 已应用状态 | `requested ≠ applied`；二者不得合并 |
| 观察到插值 | 视觉观察并非仪器化的内容证明 |
| 崩溃 / 伪影 | 稳定性和质量信号 |
| 诊断信息 | 可复现性和分级 |

未主张通用的基础 FPS 阈值；实际值会被记录，以便未来分析可以研究伪影严重程度、延迟和后端行为与基础 FPS 的关系。

## 证据分级

每个（GPU、驱动程序、游戏、API、商店、启动方式）组合映射到一个分级：

| 分级 | 含义 |
|---|---|
| `PROJECT_VALIDATED` | 由项目团队在参考配置上仪器化 / 复现 |
| `COMMUNITY_CONFIRMED` | 具有充分诊断信息的高质量外部报告 |
| `COMMUNITY_REPORTED` | 合理但仪器化不完整的用户报告 |
| `EXPERIMENTAL` | 架构 / 路径已接纳但测试不够充分 |
| `UNTESTED` | 无证据 |

维护者在审核后分配分级。单条轶事性结果绝不会被提升为 `PROJECT_VALIDATED`。

## 兼容性观测架构（可公开安全）

这是用于组织结果的公开安全记录结构。它不包含任何逆向工程内部实现。

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

一行即一个组合。同一款游戏可能以不同的商店、启动方式或结果多次出现——这是预期内的，并非矛盾。

## 社区兼容性表（结构）

项目测试结果与社区报告分开保存。经过验证的新行会随时间加入；本文档不会自动提升任何内容。

| GPU | 驱动程序 | 游戏 | 商店 | 启动 | 基础 FPS | 结果 | 证据分级 |
|---|---|---|---|---|---|---|---|
| RTX 3090 | 616.64 | Cyberpunk 2077 | Steam | Direct EXE | — | 观察到可用 | `PROJECT_VALIDATED` |

填充后的项目矩阵位于 [README](../README.zh-CN.md#tested-in-real-games)。

## 模拟器

模拟器被视为一个独立的兼容性类别，且**不**声称可用。请参阅 [EMULATOR_TEST_PLAN.zh-CN.md](EMULATOR_TEST_PLAN.zh-CN.md)；所有已测试模拟器的当前状态为 `NOT_TESTED`。
