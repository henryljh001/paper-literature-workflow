---
name: paper-literature-workflow
description: Configure literature search, screening, evidence extraction, synthesis, and method-comparison rules for the field of a target paper. Use for 总文献库、领域化检索方案、文献纳排、精读编码、分析文献集、方法比较与选取依据。Reuse existing verified records and execute only the requested scope. Route ordinary prose revision to a writing skill; this workflow does not authorize empirical analysis or formal manuscript integration.
metadata:
  version: "0.1.0"
---

# 论文领域驱动的文献工作流

先依据目标论文领域形成专用规则，再用这些规则处理文献。专业适配必须改变来源、检索式、纳排条件、精读字段或比较标准，不能只添加学科标签。

## 恢复任务与确定范围

读取适用项目规则及与当前任务有关的有效状态，明确输入、输出位置、当前写入者、已完成工作和禁止动作。具体研究结论及旧任务路由不写入本技能；项目有隔离要求时仅读取相应权限与允许材料。

先复用现有题录、判断、证据卡和规则方案。资料或状态冲突时停止依赖冲突的动作；可以继续用户已授权且不受影响的规则设计或只读审计。仅当信息无法从当前材料获得、且影响任务范围或关键判断时提出简短问题。

## 选择模式

| 模式 | 适用请求 | 交付 |
|---|---|---|
| `CONFIGURE` | 将通用方法适配到目标论文领域 | 论文任务说明、领域规则方案及其已验证/未验证状态 |
| `PROCESS` | 按已有规则检索、整理、筛选、精读、确定文献集或综合 | 指定阶段的记录、来源、决定、检查与版本 |
| `AUDIT` | 检查现有做法、文献集或证据链 | 规则—执行证据对照、范围限定的结论与问题清单 |
| `COMPARE` | 比较数据方法并形成选择依据 | 问题—证据—候选方案—条件—取舍记录 |

`继续`先恢复当前任务的有效阶段，不默认重启检索或转入旧研究方向。按用户授权范围连续完成必要步骤；既有项目人工闸门仍适用，不额外要求每个常规动作重新批准。

## CONFIGURE：先生成论文专用规则

读取 [domain-adaptation.md](references/domain-adaptation.md)，以 [paper_brief.template.json](assets/paper_brief.template.json) 和 [domain_protocol.template.json](assets/domain_protocol.template.json) 生成工作目录中的实例，保留模板不改。

1. 明确领域、论文类型、对象、研究问题、既有资产及实际允许的动作。
2. 从可追溯的领域资料提取要求，写明每条要求如何具体修改某个操作。
3. 配置来源与检索路线、纳排及待核标准、研究类型评价、精读字段和方法比较维度。
4. 检查规则是否误伤理论、方法、异质案例或反证，区分同义词与邻近概念。
5. 记录来源核验、平台语法、种子及边界案例检查是否实际完成。未运行的测试不能写通过。

规则的填写完成不等于真实检索已验证。输出可明确为规划就绪、可用于限定阶段或仍待核验，不以空字段或模拟数伪装完成。

## PROCESS：七模块按需执行

读取 [stage-contracts.md](references/stage-contracts.md)。先检查当前阶段所需的有效规则和证据，再进入用户要求的阶段；已通过且仍适用的步骤不重做。

| 模块 | 关键动作 |
|---|---|
| 总文献库整理 | 来源登记、作品身份与版本关联 |
| 文献相关性筛选 | 依据原文材料判定贡献、纳排及待核 |
| 证据核验与研究质量评价 | 按研究类型及预定用途核验内容、方法和边界 |
| 分析文献集确定 | 按具体分析用途形成可追溯成员清单 |
| 跨文献证据综合 | 比较概念、对象、时空、方法、发现与分歧 |
| 数据方法适用性比较 | 评价候选组合的必要条件与取舍 |
| 研究方案选取与论证 | 保存选择建议、备选、未选理由及实际采用状态 |

检索平台和PDF操作使用当前可用的适当工具；本技能不假设某个连接器、付费数据库、OCR或外部模型始终可用。工具不可用时报告实际限制，保留已有可用证据。

## COMPARE与AUDIT

按 [appraisal-and-selection.md](references/appraisal-and-selection.md) 区分来源报告、执行者解释和实际检验。比较单位是“问题、数据版本、测量、方法及验证条件”的组合。文献提及一种数据不证明本论文已经取得它，方法常用也不证明其前提已满足。

审计可以直接使用用户给出的准则，不要求先运行CONFIGURE。先做身份、字段、计数及关系检查，再开展与请求规模相称的语义核对。说明未覆盖部分；元数据完整不等于研究质量通过。

## 全程不变量

- 学术相关性、全文获取、分析用途和研究方案采用分别记录。
- 不因全文难取、结果相反、作者声望或预定数量目标自动决定单篇学术资格。
- 摘要背景可以保留；承重或精确主张需要相应原文证据。阅读深度不替代质量评价。
- 原始记录、独立作品、同研究多报告及证据片段分开计数；重复关系经核验后处理，原件保留。
- 关键未知保持待核；不适用说明理由；必要条件失败不能被总分抵消。
- 研究问题数量、年份范围、地区、方法及文献数量由任务配置，不硬编码到通用技能。

## 交付与验证

按需复制 [decision_log.template.csv](assets/decision_log.template.csv)、[evidence_record.template.csv](assets/evidence_record.template.csv)、[method_comparison.template.csv](assets/method_comparison.template.csv) 和 [stage_state.template.json](assets/stage_state.template.json)。仅实例化当前任务需要的表，不制造空产物套件。

对照 [verification-cases.md](references/verification-cases.md) 检查关键行为。记录可复核的输入、规则版本、输出、检查、失败次数、残留及下一动作；遵守项目已有复盘契约。区别事实、推断、建议和待裁决事项。

同一失败默认最多重试两次；项目更严格的合同优先。未通过的依赖条件不以修改措辞或换指标规避。没有新证据时不反复生成相同结果。用户要求系统框架图时使用实际图像并遵守适用的项目制图路线，不把Mermaid源码作为图片交付。
