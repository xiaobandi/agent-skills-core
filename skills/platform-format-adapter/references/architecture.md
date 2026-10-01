# 能力与字段速查

技能：`platform-format-adapter`（L1 原子技能）

## 元信息

| 字段 | 值 |
|---|---|
| 技能 ID | `skill_platform_format_adapter` |
| 目录 | `skills/platform-format-adapter` |
| 复杂度 | S |
| 阶段 | P0 |
| 可见性 | platform_shared |
| 版本 | v1.0.0 |
| 许可 | MIT |
| 验证等级 | A（自带脚本 `format_adapter.py`，已用真实夹具执行并抓取 stdout/stderr/退出码） |

## 输入契约

- **必填**：主稿（标题 + 正文）
- **必填**：目标平台列表
- **可选**：各平台历史爆款风格
- **可选**：账号人设语气

## 脚本清单

| 脚本 | 用途 | 调用方式 |
|---|---|---|
| `scripts/format_adapter.py` | 确定性执行逻辑 | `python3 scripts/format_adapter.py` |

真实调用：

```bash
python3 scripts/format_adapter.py --file examples/input/main.md --platforms '小红书,抖音'
```

## 质量门

- 每个版本都满足该平台字数上限
- 未把平台名写进正文（适配是改写不是贴标签）

## 已知陷阱

- 只改字数不改语气，等于没适配——小红书要口语和第一人称，公众号要有小标题分层
- 机械截断会把结尾的转化钩子砍掉，需人工复核

## 边界

- 不做自动发布，只产出可发布文本
