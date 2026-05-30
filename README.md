# ws63-svd

HiSilicon **WS63**（RISC-V RV32IMFC_Zicsr，Wi-Fi 6 + BLE + SLE/星闪）的手写 CMSIS-SVD 描述，
是 [`ws63-pac`](https://github.com/sanchuanhehe/ws63-pac)（经 svd2rust 生成）的上游真值。

## 内容

- `WS63.svd` — CMSIS-SVD 源（497 寄存器 / 36 外设，含 `enumeratedValues`、`derivedFrom`、`writeConstraint`、`addressBlock`）。
- `validate.py` — 对照官方 ARM CMSIS-SVD XSD 校验。
- `ws63-settings.yaml` — svd2rust 目标设置。
- `main.py` — 占位脚本（**尚未实现**生成流水线，见下）。

## 从 SVD 生成 PAC

> ⚠️ 目前**没有**可复现的自动化生成脚本。历史上 `ws63-pac/src/lib.rs` 由 svd2rust 0.37.1 生成后用
> `cargo fmt` 格式化，且后续个别寄存器是**手补**进生成代码而非重生成——下次 clean regen 可能丢失/冲突。
> 整改计划见 monorepo [ROADMAP](https://github.com/sanchuanhehe/ws63-rs/blob/main/ROADMAP.md) 阶段 2
> （提交 pin 版本的 svd2rust + form/fmt 脚本，CI 增"重生成并 diff 校验"，停止手补 lib.rs）。

手动生成（参考，待脚本化）：

```bash
svd2rust --target riscv -i WS63.svd      # 生成 lib.rs（版本需固定）
form -i lib.rs -o src/ && rm lib.rs      # 可选：拆分
cargo fmt
```

## 校验

```bash
uv run validate.py        # 对照 CMSIS-SVD XSD
```

## 架构与评审

见主仓库 <https://github.com/sanchuanhehe/ws63-rs/blob/main/docs/architecture/ws63-svd.md>。
