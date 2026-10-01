# 能力与字段速查

技能：`review-sentiment-tag`（L1 原子技能）

## 元信息

| 字段 | 值 |
|---|---|
| 技能 ID | `skill_review_sentiment` |
| 目录 | `skills/review-sentiment-tag` |
| 复杂度 | M |
| 阶段 | P0 |
| 可见性 | platform_shared |
| 版本 | v1.0.0 |
| 许可 | MIT |
| 验证等级 | A（自带脚本 `sentiment_tag.py`，已用真实夹具执行并抓取 stdout/stderr/退出码） |

## 输入契约

- **必填**：评论流（每行一条或表格）
- **可选**：历史申诉记录
- **可选**：品类专属词

## 脚本清单

| 脚本 | 用途 | 调用方式 |
|---|---|---|
| `scripts/sentiment_tag.py` | 确定性执行逻辑 | `python3 scripts/sentiment_tag.py` |

真实调用：

```bash
python3 scripts/sentiment_tag.py --file examples/input/reviews.txt
```

## 质量门

- P0 条目全部可定位到原文
- 反讽类被单独标注（基线易误判）

## 已知陷阱

- '物流慢但东西好'是混合情绪，单纯二分会失真
- 反讽（'真是太好了呵呵'）基线必错，必须人工复核

## 边界

- 不做用户身份识别或人肉
