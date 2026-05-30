# ws63-svd 架构

本仓库是 [ws63-rs](https://github.com/sanchuanhehe/ws63-rs) monorepo 的子模块。

`ws63-svd` 是手写的 CMSIS-SVD 源（`WS63.svd`）+ 校验工具（`validate.py`），是 [`ws63-pac`](https://github.com/sanchuanhehe/ws63-pac)
的上游真值，经 svd2rust 生成 PAC。

完整架构与评审（集中维护于主仓库）：
- 组件文档：<https://github.com/sanchuanhehe/ws63-rs/blob/main/docs/architecture/ws63-svd.md>
- 总体架构：<https://github.com/sanchuanhehe/ws63-rs/blob/main/docs/architecture/overview.md>
- 整改排期：<https://github.com/sanchuanhehe/ws63-rs/blob/main/ROADMAP.md>

> 已知问题：尚无可复现的 svd2rust 生成流水线（`main.py` 是占位桩），寄存器曾被手补进生成代码而非重生成。
> 见 ROADMAP 阶段 2。
