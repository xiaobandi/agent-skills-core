# agent-skills-core

> 平台公共原子技能 + 共享 TOOL + 连接器契约。
> **被 ≥2 个数字员工复用的能力沉淀在这里**，员工仓库以外部依赖方式引用，不复制正文。

![version](https://img.shields.io/badge/version-1.0.0-blue)
![license](https://img.shields.io/badge/license-MIT-green)
![skills](https://img.shields.io/badge/skills-26-purple)

## 为什么要有这一层

30 个数字员工里有大量重复能力——「简报生成」被 10 个员工用到，
「平台合规词扫描」被 6 个用到。如果每个员工仓库各存一份，
改一次要改 N 遍，改漏一处就产生行为漂移。

所以定了一条硬规则：

> **被 ≥2 个数字员工引用的能力，必须公共化到这里。**

## 内容

| 目录 | 内容 | 数量 |
|---|---|---|
| `skills/` | 公共原子技能 | 26 |
| `tools/` | 共享确定性脚本 | 9 |
| `connectors/` | 连接器定义与契约 | 12 |
| `specs/` | 有意不公共化的复用能力（Spec + Mock + 权限声明） | 1 |
| `schemas/` | 机器可校验的 JSON Schema | 2 |

## 公共技能清单

| 技能 | slug | 复用员工数 | 复杂度 | 阶段 | 成熟度 |
|---|---|---|---|---|---|
| `归因分析` | `attribution-analysis` | 4 | M | P2 | 契约完备 |
| `简报生成` | `brief-generator` | 10 | S | P1 | 已实现 |
| `口语化改写` | `colloquial-rewrite` | 2 | S | P0 | 已实现 |
| `差评安抚话术` | `complaint-soothe` | 3 | S | P0 | 已实现 |
| `平台合规词扫描` | `compliance-word-scan` | 8 | M | P0 | 已实现 |
| `转化结构模板` | `conversion-structure-template` | 2 | S | P1 | 契约完备 |
| `文案排版` | `copy-layout` | 3 | S | P2 | 已实现 |
| `优惠券策略` | `coupon-strategy` | 2 | S | P1 | 契约完备 |
| `文档问答（RAG）` | `doc-qa-rag` | 3 | M | P2 | 已实现 |
| `粉丝分层打标` | `fan-segment-tag` | 2 | S | P1 | 已实现 |
| `团购文案生成` | `groupbuy-copy-writer` | 2 | S | P0 | 契约完备 |
| `钩子文案` | `hook-copy` | 3 | S | P0 | 已实现 |
| `朋友圈文案生成` | `moments-copy-writer` | 2 | S | P1 | 契约完备 |
| `多语言写作` | `multilingual-writing` | 3 | S | P0 | 契约完备 |
| `人设语气库` | `persona-tone-lib` | 3 | S | P0 | 已实现 |
| `平台格式适配` | `platform-format-adapter` | 6 | S | P0 | 已实现 |
| `价格监控` | `price-monitor` | 2 | M | P1 | 已实现 |
| `回复话术生成` | `reply-copy-generator` | 4 | S | P0 | 已实现 |
| `评论情绪识别` | `review-sentiment-tag` | 5 | M | P0 | 已实现 |
| `RFM 分层` | `rfm-segmentation` | 2 | S | P2 | 契约完备 |
| `定时排期` | `scheduled-dispatch` | 6 | S | P1 | 已实现 |
| `脚本结构生成` | `script-structure` | 3 | S | P0 | 已实现 |
| `标题生成` | `title-generator` | 4 | S | P1 | 已实现 |
| `选题查重` | `topic-duplicate-check` | 2 | S | P0 | 契约完备 |
| `选题知识库管理` | `topic-kb-manage` | 3 | S | P0 | 已实现 |
| `爆款结构分析` | `viral-structure-analysis` | 2 | S | P1 | 已实现 |

## 有意不公共化的能力

| 能力 | slug | 复用员工数 | 理由 |
|---|---|---|---|
| `数据对接` | `data-ingest-adapter` | 5 | 报告明确"数据采集连接器族不公共化为 SKILL"——开源侧只发 Spec + Mock + 权限声 |

这些能力因为与外部平台接口强绑定，做成公共 SKILL 会让一份提示词同时适配 N 个平台，
反而更难维护。因此只在 `specs/` 发契约，实现留在各员工仓库的绑定层。

## 怎么用

```bash
git clone <本仓库地址> agent-skills-core
```

然后在员工仓库的会话里把 `agent-skills-core/skills` 一并挂载为技能目录。
每个员工用到的公共技能与版本，在它自己的 `dependencies.yaml` 里锁定。

## 版本与兼容

- 当前 `v1.0.0`。员工仓库按 `v1.0.0` 锁定依赖。
- 破坏性变更必须升 minor 以上，并在 `CHANGELOG.md` 给出迁移说明。

## 测试

```bash
pip install pyyaml && python3 tests/run.py
```

## 许可

MIT，详见 [`LICENSE`](LICENSE)。
