# 能力与字段速查

技能：`colloquial-rewrite`（L1 原子技能）

## 元信息

| 字段 | 值 |
|---|---|
| 技能 ID | `skill_colloquial_rewrite` |
| 目录 | `skills/colloquial-rewrite` |
| 复杂度 | S |
| 阶段 | P0 |
| 可见性 | platform_shared |
| 版本 | v1.0.0 |
| 许可 | MIT |
| 验证等级 | A（自带脚本 `compliance_scan.py`，已用真实夹具执行并抓取 stdout/stderr/退出码） |

## 输入契约

- **必填**：待改写文稿
- **可选**：目标语气（朋友聊天 / 专业口播）
- **可选**：人设语气库

## 脚本清单

| 脚本 | 用途 | 调用方式 |
|---|---|---|
| `scripts/compliance_scan.py` | 确定性执行逻辑 | `python3 scripts/compliance_scan.py` |

真实调用：

```bash
python3 scripts/compliance_scan.py --file examples/input/formal.txt --platform 抖音
```

## 质量门

- 事实、数字、专有名词未被改动
- 口语化后仍然专业可信，未变成'油腻'

## 已知陷阱

- 口语化不等于加'家人们''绝绝子'——过度网络用语会透支账号可信度
- **口播稿要换气** —— 句子要按呼吸长度切，书面标点不够用

## 边界

- 不改写事实性内容；原文信息缺失时提问而非脑补
