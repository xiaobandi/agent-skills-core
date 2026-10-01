# 能力与字段速查

技能：`title-generator`（L1 原子技能）

## 元信息

| 字段 | 值 |
|---|---|
| 技能 ID | `skill_title_generate` |
| 目录 | `skills/title-generator` |
| 复杂度 | S |
| 阶段 | P0 |
| 可见性 | platform_shared |
| 版本 | v1.0.0 |
| 许可 | MIT |
| 验证等级 | A（自带脚本 `title_gen.py`，已用真实夹具执行并抓取 stdout/stderr/退出码） |

## 输入契约

- **必填**：选题或内容主题
- **可选**：平台
- **可选**：受众
- **可选**：关键词
- **可选**：历史高点击标题

## 脚本清单

| 脚本 | 用途 | 调用方式 |
|---|---|---|
| `scripts/title_gen.py` | 确定性执行逻辑 | `python3 scripts/title_gen.py` |

真实调用：

```bash
python3 scripts/title_gen.py --topic 'AI 帮做小红书选题' --platform 小红书 --audience '自媒体新手' --n 6
```

## 质量门

- 所有标题都在平台字数上限内
- 推荐标题不含极限词

## 已知陷阱

- 标题与内容不符是掉推荐的主因
- 数字堆砌（'3个方法5个技巧7个坑'）已被受众脱敏，慎用

## 边界

- 不生成标题党式虚假标题
