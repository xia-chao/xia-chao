# Xia Chao · 夏超

**Rust / WebAssembly / Systems Engineering**

专注 Rust 运行时、编译器与云基础设施，正在寻找 Rust 开发工程师机会。持续开发个人系统项目，并长期贡献 Wasmtime 与 Cloud Hypervisor。

## 个人项目：从设计到验证

### NGWI · WebAssembly 解释执行引擎

个人研究项目（Next-Generation WebAssembly Interpreter），独立设计 Rust 执行内核与多模块运行时。

- 使用 wasmparser 解析与验证，自行实现数值、控制流、SIMD、内存、表与引用、调用、GC 和异常等执行语义。
- 以显式帧栈和统一 Store 处理跨实例调用、导入共享与类型/对象身份；实现 fuel、内存和调用深度等资源限制。
- 开发可选寄存器解释路径和受限 macOS/AArch64 整数函数原生后端，默认保持解释执行。
- 固定版本验收归档：258 份官方 Core 3.0 WAST 文件、65,308 条指令/断言记录全部通过；另有 695 个自编用例和 76 个 Store 场景步骤通过。结果对应归档版本与测试配置。

### [HeteroWasm · Wasm → WebGPU 编译器](https://github.com/xia-chao/HeteroWasm)

使用 Rust 构建保守的循环编译与执行原型，将通过合法性检查的受支持整数循环转换为 WGSL 计算着色器，保留原始 Wasm 的 CPU 路径。

- 将 IR、控制流、标量演化、地址恢复、依赖分析、合法性检查、代码生成、运行时与 CLI 拆分为 14 个 crate。
- 集成 Wasmtime 与 wgpu，串联模块分析、内核生成、缓冲区传输和执行调度。
- 以 CPU 执行为参照逐字节比较完整内存，先核验结果，再进行重复基准计时。

## 大型 Rust 项目：持续上游协作

### [Wasmtime](https://github.com/bytecodealliance/wasmtime)

持续参与功能开发、正确性修复、回归测试与上游评审，近期代表成果：

- [HTTP/2 连接支持 · #14908](https://github.com/bytecodealliance/wasmtime/pull/14908)：基于 Tokio、Hyper/Hyper-util 接入 wasmtime serve 并补充集成测试。
- [WASI 输出流写入额度约束 · #14966](https://github.com/bytecodealliance/wasmtime/pull/14966)：完善 c-api、sink 和文件输出流的 check-write 约束。
- [持续更新的贡献记录](https://github.com/bytecodealliance/wasmtime/pulls?q=is%3Apr+author%3Axia-chao)

### [Cloud Hypervisor](https://github.com/cloud-hypervisor/cloud-hypervisor)

持续参与虚拟化基础设施开发，近期代表成果：

- [VHDX 元数据区域保护 · #9198](https://github.com/cloud-hypervisor/cloud-hypervisor/pull/9198)：拒绝非法 payload BAT 重叠映射，补充读写路径校验与回归测试。
- [QCOW2 数据语义修复 · #9162](https://github.com/cloud-hypervisor/cloud-hypervisor/pull/9162)：修复 backing file 场景下 discard/write-zeroes 可能暴露底层数据的问题。
- [持续更新的贡献记录](https://github.com/cloud-hypervisor/cloud-hypervisor/pulls?q=is%3Apr+author%3Axia-chao)

以上为近期精选，贡献范围持续扩展；2026 年 8 月已有 Effect、NestJS、Electron、Svelte、Angular、Tauri 等项目的获合并贡献。

## 工程实践与社区认可

- 全栈项目实践：手机 APP、服务端及 Rust/Tauri 桥接协同开发，关注分层架构、类型契约、事务一致性、幂等、权限边界与异常恢复。
- 验证方式：规范测试、边界用例、结果对照、可复查运行归档与上游代码评审。
- **Bytecode Alliance Recognized Contributor（RC）**：[由 Pat Hickey 提名并经 TSC 认可](https://github.com/bytecodealliance/governance/pull/165)；依[联盟章程](https://github.com/bytecodealliance/governance/blob/main/TSC/charter.md#recognized-contributors)，享有 TSC 代表及董事会 At-Large 董事选举的提名与投票权。

技术关键词：Rust · WebAssembly · WASI · Tokio · Hyper · wgpu · WGSL · Tauri · PostgreSQL · Linux
