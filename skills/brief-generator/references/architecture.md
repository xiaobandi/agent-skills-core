# 能力与字段速查

技能：`brief-generator`（L1 原子技能）

## 元信息

| 字段 | 值 |
|---|---|
| 技能 ID | `skill_brief_generator` |
| 目录 | `skills/brief-generator` |
| 复杂度 | S |
| 阶段 | P0 |
| 可见性 | platform_shared |
| 版本 | v1.0.0 |
| 许可 | MIT |
| 验证等级 | A（自带脚本 `brief_render.py`，已用真实夹具执行并抓取 stdout/stderr/退出码） |

## 输入契约

- **必填**：原始数据或事件列表
- **必填**：简报类型（日报/周报/战报/月报）
- **可选**：读者角色
- **可选**：关注指标优先级
- **可选**：上一期简报

## 脚本清单

| 脚本 | 用途 | 调用方式 |
|---|---|---|
| `scripts/brief_render.py` | 确定性执行逻辑 | `python3 scripts/brief_render.py` |

真实调用：

```bash
python3 scripts/brief_render.py --kind brief --file examples/input/brief.json --title '今日经营简报'
```

## 质量门

- 有且只有一句结论，放在最前
- 每条风险都配了动作或负责人
- 没有'待填'残留段

## 已知陷阱

- 罗列数据不等于简报，缺结论的简报等于没写
- 数据口径不一致（周报按自然周还是滚动 7 天）要先对齐，否则前后期不可比

## 边界

- 只做汇总与呈现，不做数据采集；数据来源需用户提供或由上游技能产出
