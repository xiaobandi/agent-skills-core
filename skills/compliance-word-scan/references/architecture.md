# 能力与字段速查

技能：`compliance-word-scan`（L1 原子技能）

## 元信息

| 字段 | 值 |
|---|---|
| 技能 ID | `skill_platform_compliance_scan` |
| 目录 | `skills/compliance-word-scan` |
| 复杂度 | S |
| 阶段 | P0 |
| 可见性 | platform_shared |
| 版本 | v1.0.0 |
| 许可 | MIT |
| 验证等级 | A（自带脚本 `compliance_scan.py`，已用真实夹具执行并抓取 stdout/stderr/退出码） |

## 输入契约

- **必填**：待检文案（或图片 OCR 后的文本）
- **必填**：目标平台
- **可选**：商品类目
- **可选**：历史违规记录
- **可选**：平台最新规则清单

## 脚本清单

| 脚本 | 用途 | 调用方式 |
|---|---|---|
| `scripts/compliance_scan.py` | 确定性执行逻辑 | `python3 scripts/compliance_scan.py` |

真实调用：

```bash
python3 scripts/compliance_scan.py --file examples/input/draft.txt --platform 淘宝
```

## 质量门

- 每条命中都能定位到原文片段
- 替换建议本身不含新的风险词
- OCR 不确定的内容已显式标注，未被静默当成无误

## 已知陷阱

- **语境豁免** —— '最好喝的一家店'（口语表达）与 '最好'（绝对化用语）风险不同，不要一律替换
- 平台规则会变，脚本词表是基线不是全集；上线前用 --lexicon 补充最新词
- 只扫文字不扫图会漏掉图上大字——图片合规是重灾区

## 边界

- 不替代平台官方审核，只做发布前自查
- 不判断商标/专利侵权等法律问题，遇到标注并转人工
