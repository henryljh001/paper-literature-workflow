# 领域要求转化为可执行规则

## 输入与依据

需要知道论文领域及具体问题、论文类型、分析对象、已有库与有效规则、请求的动作和输出范围。未知项保留null或待核；已有状态能提供的信息不反复问用户。新检索的实际来源、时间范围与语法未明确时，先完成方案，不冒充已运行检索。

领域依据可以来自用户授权的概念原典、代表性综述、方法文献及适用指南。写明来源与定位，以及它支持哪条规则。保留领域内部争论；模型记忆、期刊声望和某篇范文不是默认的全领域强制标准。外部查证仅发送允许公开的信息。

## 要求到规则的转换表

每条 `requirements_mapping` 至少包含要求、来源依据、适用研究类型、被修改的环节、具体操作、验证方式与当前核验状态。

| 需要适配的内容 | 产物 | 必要约束 |
|---|---|---|
| 成果载体与来源 | 来源计划及补充发现路径 | 一个平台可含多类资料；回溯追引是发现路径，不重复计作品 |
| 概念与术语 | 同义、邻近、歧义概念组 | 检索扩展不等于概念等价；跨语种单独核验 |
| 检索结构 | 面向不同问题/理论/方法的检索路线 | 不把论文题名全部词汇统一AND，理论方法可有独立路线 |
| 学术贡献 | 纳入、排除、背景和待核标准 | 前期至少一项相关贡献；最终用途再收束 |
| 证据与研究类型 | 全文触发及类型化评价 | 理论、质性、定量、规范性研究不共用单一淘汰表 |
| 专业比较条件 | 提取字段与比较准则 | 概念、单元、时间、材料及方法条件可追溯 |

问题框架如PICO、PEO或SPICE按任务适用性选用，不能要求每篇或每条检索路线使用同一框架。采用指南时记录其适用范围，不将医学干预标准直接当作其他领域的通用标准。

## 生成规则方案

由任务说明生成 `domain_protocol.json`，保存在本次工作目录，包含以下内容：

1. 来源与检索路线：源、字段、概念组、表达式、时间范围、语言/类型处理、为何该路线必要。
2. 纳排规则：相关学术功能、全库排除、特定用途不适用、背景与待核、触发全文的条件。
3. 精读要求：通用字段加领域特有概念、单元、材料和可比性字段，注明适用研究类型。
4. 质量与方法比较：每项必要条件、证据位置、允许解释及补证要求。
5. 验证范围：资料核验、平台语法和种子/边界例检查的实际状态。

数组记录的最小结构如下；可按任务增加字段，但不要让同一字段混装规则、决定与日志：

| 数组 | 每条记录至少包含 |
|---|---|
| field_requirements | id、requirement、source、locator、applicable_study_types、verification_status |
| requirements_mapping | requirement_id、operation、rule_change、rationale、check_method |
| source_plan | source_id、source_type、platform_or_location、role、scope、access_status |
| search_routes | route_id、purpose、concept_groups、query、platform、time_scope、syntax_status、validation_evidence |
| eligibility各子数组 | rule_id、condition、applicable_use、reason_code、required_evidence |
| study_type_appraisal | study_type、use、criterion、required_evidence、on_missing |
| extraction_fields | name、meaning、applicable_study_types、source_requirement、missing_value_rule |
| comparison_criteria | criterion_id、criterion、applicable_question、is_necessary、required_evidence |

模板里的空数组只是未配置状态，不能被解释为无需标准。具体无关字段可注明不适用及理由；实际运行不得只留下“专业化”“遵循规范”等无法执行的占位表达。

不得以“增加专业性”这样的抽象要求代替具体规则修改；至少说明改了哪条来源、检索、筛选或比较动作及理由。若当前材料不能支持一项专业规则，将其列为待核建议，保留其他可用部分。

## 应用与修订

`status=DRAFT`表示规则尚待完成或核验，不禁止读者审阅。`READY_FOR_BOUNDED_USE`仅用于已列明范围和验证条件的动作，不是全链条放行。`validated_operations`只写实际得到支持的操作；平台语法未测时不得据此声称可直接执行该平台检索。

已授权读取现有记录、按明确内容标准进行有限筛选，不一定需要新检索或平台测试。按阶段需要判断依赖，避免无关未验证项阻断独立工作。

领域、问题或纳排原则变化时，生成新协议版本、说明差异及受影响记录。不得覆盖旧失败或选择记录。文献库规模不作为新版本必须达到的目标。

## 示例边界

人文地理的领域适配可能新增地域/节点边界、空间层级、人口与用地概念以及格局/过程检查；其理论方法来源可独立于人口主题检索。这些是示例，不自动用于其他论文。教育质性研究可能需要情境、参与者、研究者位置与解释证据；不能因缺回归模型而排除。实际规则须由该任务的领域依据支持。
