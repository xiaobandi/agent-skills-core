# 能力与字段速查

技能：`topic-kb-manage`（L1 原子技能）

## 元信息

| 字段 | 值 |
|---|---|
| 技能 ID | `skill_topic_kb_manage` |
| 目录 | `skills/topic-kb-manage` |
| 复杂度 | S |
| 阶段 | P0 |
| 可见性 | platform_shared |
| 版本 | v1.0.0 |
| 许可 | MIT |
| 验证等级 | A（自带脚本 `kb_manage.py`，已用真实夹具执行并抓取 stdout/stderr/退出码） |

## 输入契约

- **必填**：操作类型（新增/查询/更新/导出）
- **可选**：选题内容
- **可选**：标签
- **可选**：权重
- **可选**：使用记录

## 脚本清单

| 脚本 | 用途 | 调用方式 |
|---|---|---|
| `scripts/kb_manage.py` | 确定性执行逻辑 | `python3 scripts/kb_manage.py` |

真实调用：

```bash
python3 scripts/kb_manage.py --db examples/input/kb.json add --title '通勤保温杯实测' --tags '产品,测评' --weight 3
python3 scripts/kb_manage.py --db examples/input/kb.json add --title '办公室喝热水指南' --tags '场景,科普' --weight 2
python3 scripts/kb_manage.py --db examples/input/kb.json add --title '保温原理 3 秒讲清' --tags '科普' --weight 1
python3 scripts/kb_manage.py --db examples/input/kb.json list --top 5
```

## 质量门

- 新增前做过查重
- 权重变更留下了理由

## 已知陷阱

- 库以 JSON 文本落盘，天然可 git 版本化——不要把库塞进某个不透明的数据库
- 只增不删会让库膨胀到不可用，需定期按权重与时效清理

## 边界

- 不做自动采集，采集由上游技能负责
