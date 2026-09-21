[English](EMULATOR_TEST_PLAN.md) | 简体中文 | [Español](EMULATOR_TEST_PLAN.es-419.md)

# 模拟器测试计划

状态：**NOT_TESTED。** 模拟器被视为一个独立的兼容性类别。在存在真实测试之前，**不**声称支持模拟器。

## 法律 / 范围

- 仅测试**用户已依法安装并配置**的软件。
- **不要**提供、请求或协助获取受版权保护的固件、密钥、BIOS 文件或游戏。
- 如果测试者自己的机器上存在依法配置的 Switch 模拟器，它可以像任何其他渲染器一样被测试；否则跳过。

## 初始模拟器集

| 模拟器 | 状态 |
|---|---|
| RPCS3 | `NOT_TESTED` |
| DuckStation | `NOT_TESTED` |
| PCSX2 | `NOT_TESTED` |
| Cemu | `NOT_TESTED` |
| Switch 模拟器（如依法安装） | `NOT_TESTED` |
| 其他 | `NOT_TESTED` |

## 逐模拟器问题

对每个模拟器，确定并记录：

1. **渲染 API**——模拟器配置使用的 API。
2. **实际呈现 API**——实际呈现的 API（可能与渲染 API 不同）。
3. **层路径**——链路中的转换层及其顺序。
4. **NvPresent 附加**——是否到达驱动程序呈现后端。
5. **Smooth 状态**——已请求和已应用。
6. **生成的插值观测**——视觉观察，明确区别于仪器化的内容证明。
7. **生命周期行为**——进程模型、设备/交换链创建、重置、交换链重建。
8. **基础 FPS**——近似实际值。
9. **伪影行为**——类型、严重程度、条件。

## 报告格式

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

## 规则

- **不要**将「模拟器能启动」归结为「Smooth Motion 已验证」。
- 只有在描述过的（GPU、驱动程序）配置上完成一次真实的、有描述测试后，才在此报告某个模拟器。
- 在真实结果出现之前，不向 README 添加任何推测性的模拟器徽章或支持声明。
