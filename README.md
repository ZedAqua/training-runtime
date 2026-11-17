# training-runtime

训练运行时与基础设施仓库，负责把训练框架、推理引擎、GPU 资源和 checkpoint 生命周期组织成可重复运行的训练任务。

## 职责

- 维护 AReaL/verl 等训练框架的适配和必要改造。
- 管理 FSDP、Megatron、LoRA、RL 配置及训练启动器。
- 维护 vLLM/SGLang 训练采样协同、权重同步和资源调度配置。
- 提供容器、GPU 环境、日志、指标和 checkpoint 管理入口。
- 记录经过验证的框架、驱动、CUDA、模型和硬件组合。

## 不负责

- 不维护 Hermes 的业务工具和 MCP 任务环境。
- 不维护数据清洗、去污染和样本发布流程。
- 不把模型权重、checkpoint 或运行日志直接提交到 Git。

## 依赖关系

训练数据通过 `training-data` 发布的 manifest 获取；Hermes 交互环境通过 `hermes-harness` 提供；评测回归由 `model-eval` 执行。

## 计划目录

```text
configs/       训练和采样配置
runtime/       框架适配与运行时改造
launchers/     单机、集群和容器启动器
containers/    镜像与依赖锁定
checkpoint/    checkpoint 元数据和生命周期脚本
monitoring/    日志、指标和故障诊断
docs/          硬件与版本兼容矩阵
```
