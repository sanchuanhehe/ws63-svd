# ws63-svd 架构

本仓库是 [ws63-rs](https://github.com/sanchuanhehe/ws63-rs) monorepo 的子模块。

`ws63-svd` 是手写的 CMSIS-SVD 源（`WS63.svd`）+ 校验工具（`validate.py`）+ 可复现生成流水线
（`regen.sh` / `postprocess.py`），是 [`ws63-pac`](https://github.com/sanchuanhehe/ws63-pac) 的上游真值，
经 svd2rust 生成 PAC。

完整架构与评审（集中维护于主仓库）：
- 组件文档：<https://github.com/sanchuanhehe/ws63-rs/blob/main/docs/architecture/ws63-svd.md>
- 总体架构：<https://github.com/sanchuanhehe/ws63-rs/blob/main/docs/architecture/overview.md>
- 整改排期：<https://github.com/sanchuanhehe/ws63-rs/blob/main/ROADMAP.md>

> 生成：`bash regen.sh` 由 `WS63.svd` 可复现生成 `ws63-pac/src/lib.rs`（svd2rust 0.37.1 + 确定性后处理
> + cargo fix/fmt，幂等，内建 build+clippy 门禁）。**勿手改生成产物**——改 SVD 后重跑 `regen.sh`。
