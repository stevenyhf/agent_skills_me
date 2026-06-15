name
platform-skill

version
1.0

description
一键调用的技术委员会圆桌技能，集成马斯客(马斯克)、张一鸣、乔布斯、黄仁勋、梁文锋、雷军、亚里士多德七位全球技术领域思想家，自动启动圆桌对话流程，针对技术类问题完成多人格观点采集、碰撞、形成专业决议报告并保存到本地。遵循Roundtable Agent Protocol v1.0协议。

trigger
中文触发词：技术委员会开会、技术委员会讨论、请技术委员会分析、platform-skill 技术问题、启动技术委员会、用技术委员会分析；
场景触发：所有技术领域问题，用户指定使用platform-skill或技术委员会skill时自动触发。

tags
技术委员会
圆桌对话
多人格
技术分析
决议报告
platform-skill

committee-members

- masike-method（马斯克·第一性原理）
- zhangyiming-method（张一鸣·延迟满足/算法效率）
- qiaobusi-method（乔布斯·完美主义/产品洞察力）
- huangrenxun-method（黄仁勋·产业周期/技术落地）
- liangwenfeng-method（梁文锋·深度求索/开源AI）
- leijun-method（雷军·互联网思维/用户导向）
- aristotle-method（亚里士多德·逻辑推理/四因说）

host: dialogue-master
report_generator: researcher-yhf
execution_flow: 自动解析用户的技术问题，以7位固定成员启动标准圆桌对话流程，完成：

1. 并行采集所有成员独立观点
2. Dialogue Master主持观点碰撞
3. researcher-yhf生成标准化技术决议报告
4. 保存报告到~/文档/技术委员会-{话题关键词}-{日期}.md

安装日期：2026-06-15
维护责任：用户自建skills体系
