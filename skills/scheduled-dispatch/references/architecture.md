# 能力与字段速查

技能：`scheduled-dispatch`（L1 原子技能）

## 元信息

| 字段 | 值 |
|---|---|
| 技能 ID | `skill_scheduled_dispatch` |
| 目录 | `skills/scheduled-dispatch` |
| 复杂度 | S |
| 阶段 | P0 |
| 可见性 | platform_shared |
| 版本 | v1.0.0 |
| 许可 | MIT |
| 验证等级 | A（自带脚本 `schedule_plan.py`，已用真实夹具执行并抓取 stdout/stderr/退出码） |

## 输入契约

- **必填**：内容池或任务池
- **必填**：起始日期
- **可选**：各平台最佳发布时段
- **可选**：人力约束
- **可选**：节假日规则

## 脚本清单

| 脚本 | 用途 | 调用方式 |
|---|---|---|
| `scripts/schedule_plan.py` | 确定性执行逻辑 | `python3 scripts/schedule_plan.py` |

真实调用：

```bash
python3 scripts/schedule_plan.py --pool examples/input/pool.json --start 2026-09-29 --days 7
```

## 质量门

- 同一天同一平台不重复排
- 时间落在该平台受众活跃窗口内

## 已知陷阱

- 排期不是承诺——素材未就绪时要能一键回退，需标出'素材依赖'
- 跨时区发布（出海场景）要显式换算，别按本地时间排

## 边界

- 真正的定时执行依赖平台能力；本技能只产出计划
