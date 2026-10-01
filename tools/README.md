# 共享 TOOL

被 ≥2 个数字员工仓库引用的确定性脚本集中在这里，避免每个员工仓库各存一份。

| 脚本 | 说明 |
|---|---|
| `anomaly_detect.py` | 来自 agent-skills-library 共享脚本库 |
| `brief_render.py` | 来自 agent-skills-library 共享脚本库 |
| `check_env.py` | （脚本文件待补） |
| `compliance_scan.py` | 来自 agent-skills-library 共享脚本库 |
| `format_adapter.py` | 来自 agent-skills-library 共享脚本库 |
| `kb_manage.py` | 来自 agent-skills-library 共享脚本库 |
| `schedule_plan.py` | 来自 agent-skills-library 共享脚本库 |
| `sentiment_tag.py` | 来自 agent-skills-library 共享脚本库 |
| `title_gen.py` | 来自 agent-skills-library 共享脚本库 |

## 约束

- 只读输入、纯函数、无网络副作用（除显式声明的抓取类）
- 不依赖第三方包（仅标准库），保证在任何环境都能跑
- 每个脚本都要能被单测直接调用
