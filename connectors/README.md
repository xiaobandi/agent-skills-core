# 连接器定义

本目录只放**定义与契约**（能力、权限、合规边界、降级方式），不放凭证。

| id | 名称 | 类别 | 访问 | 提供方 | 合规边界 |
|---|---|---|---|---|---|
| `conn_category_lib` | 平台类目库 | 电商 | read | 各电商平台类目/属性表 | 类目映射为只读参考；一次维护多店复用… |
| `conn_content_platform` | 内容平台发布与数据 | 内容 | semi | 小红书/抖音/视频号 | 发布走草稿 + 人工确认；数据回捞遵守平台规则，不绕过风控… |
| `conn_ecom_platform` | 电商平台商品/订单 | 电商 | read | 淘宝/抖店/拼多多/快手 | 商品与订单只读；上架草稿需人工确认后提交（write_reserved）… |
| `conn_image_gen` | 图像生成模型 API | 多模态 | read | 文生图 / 图生图 | 须确认商用授权；产出须标注 AI 合成；拒绝侵权与夸大功效… |
| `conn_llm_inference` | LLM 推理 API | 运行层 | read | 多供应商可替换（开源/低价模型兜底 + 商用 API 分层） | 不做模型选型锁定；模型是可替换燃料… |
| `conn_logistics` | 物流查询 | 电商 | read | 快递 100 / 平台物流接口 | 只读查询，不做改单、不做拦截… |
| `conn_ocr` | OCR 文字识别 | 多模态 | read | 通用 OCR | 图内文案识别结果仅用于合规检测，不外传原图… |
| `conn_payment` | 支付平台流水 | 财务 | read | Stripe/Paddle/支付宝 | 只读流水；发票与台账仅做归类整理，不做申报决策… |
| `conn_platform_review` | 平台评价读取 | 电商/本地 | semi | 美团/大众点评/抖音生活服务/电商平台 | 接口多为只读或半开放；无 API 时改商家导出 CSV；严禁爬取与诱导删评话术… |
| `conn_publish_endpoint` | 平台发布端点（Coze/Dify/WorkBuddy） | 分发 | write_reserved | 智能体平台导入接口 | 资产以标准 SKILL.md / manifest 格式导入；不绑定单一平台… |
| `conn_rag_kb` | RAG 知识检索 | 运行层 | read | 向量库 + 文档解析 | 知识库按资产包隔离，禁止跨包串联客户数据… |
| `conn_wecom` | 企业微信私域 | 私域 | semi | 企微 API / 客服 | 触达频率受控，遵守隐私与平台规则；严禁骚扰与诱导… |

## 绑定方式

员工仓库在自己的 `connectors/bindings.yaml` 里引用这些 id 并声明 scope。
凭证一律通过环境变量注入。
