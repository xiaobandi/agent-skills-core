# 能力与字段速查

技能：`price-monitor`（L1 原子技能）

## 元信息

| 字段 | 值 |
|---|---|
| 技能 ID | `skill_price_monitor` |
| 目录 | `skills/price-monitor` |
| 复杂度 | M |
| 阶段 | P1 |
| 可见性 | platform_shared |
| 版本 | v1.0.0 |
| 许可 | MIT |
| 验证等级 | A（自带脚本 `anomaly_detect.py`，已用真实夹具执行并抓取 stdout/stderr/退出码） |

## 输入契约

- **必填**：竞品价格数据（含时间戳）
- **可选**：自身定价
- **可选**：成本
- **可选**：监控阈值

## 脚本清单

| 脚本 | 用途 | 调用方式 |
|---|---|---|
| `scripts/anomaly_detect.py` | 确定性执行逻辑 | `python3 scripts/anomaly_detect.py` |

真实调用：

```bash
python3 scripts/anomaly_detect.py --file examples/input/metrics.json
```

## 质量门

- 到手价与标价口径统一
- 建议未违反价格法（如串通定价）

## 已知陷阱

- 到手价含券，凭标价对比会误判
- 短期促销与长期调价要分开看

## 边界

- 不做串通定价等违反价格法的建议
