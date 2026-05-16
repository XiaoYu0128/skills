# Skills

这个仓库用于集中管理可复用的 Codex skills。目录按使用场景分类，打开仓库后可以先看分类，再进入具体 skill。

## 分类

| 分类 | 目录 | 适合处理的问题 |
| --- | --- | --- |
| 交付与验收材料 | [delivery/](delivery/) | 根据功能范围、提交记录、接口变更或截图整理正式交付文档、测试材料、验收报告和运维手册。 |
| 架构与方案图片 | [arch-diagram-style/](arch-diagram-style/) | 为技术方案、投标文档或系统设计文档生成和调整架构图、数据模型图、部署拓扑图，并保持统一图面风格。 |
| 项目开发治理与规划 | [project-dev-governance/](project-dev-governance/)、[planning-with-files-zh/](planning-with-files-zh/)、[planning-and-task-breakdown/](planning-and-task-breakdown/) | 面向项目开发过程，整理需求基线、拆分迭代任务、控制变更、持续跟踪阶段计划和执行动作。 |

## 当前 Skills

| Skill | 位置 | 一句话说明 | 典型产物 |
| --- | --- | --- | --- |
| 交付材料整理 | [delivery/delivery-materials/](delivery/delivery-materials/) | 面向软件项目交付，把零散需求、代码变更、接口说明和截图整理成业主可读的正式材料。 | 用户使用手册、功能测试、性能测试、测试验收报告、运维手册、Word 文档。 |
| 架构图风格与出图约束 | [arch-diagram-style/](arch-diagram-style/) | 面向技术方案图片生产，沉淀标题栏、分层容器、卡片、箭头、排版避坑和终版样例，支持继续出第三章这类架构图与数据模型图。 | 业务协同架构图、分系统能力图、数据模型图、总体部署与运行保障图、图片参考规则。 |
| 项目开发治理 | [project-dev-governance/](project-dev-governance/) | 面向项目开发管理，整理开发前材料、需求清单、迭代划分、变更控制和交付检查点。 | 开发前需求清单、功能总台账、Sprint 拆分建议、变更识别结果、阶段风险清单。 |
| 文件化持续规划（中文） | [planning-with-files-zh/](planning-with-files-zh/) | 面向长期项目推进，把计划、当前状态、下一步动作持续沉淀到 markdown 文件中。 | 阶段计划文件、执行跟踪记录、待办事项、持续更新的项目推进文档。 |
| 任务拆解与计划分解 | [planning-and-task-breakdown/](planning-and-task-breakdown/) | 面向单次目标拆解，把一个较大的交付目标细化成可执行、可排序、可检查的任务列表。 | 任务分解清单、阶段步骤、检查点列表、具体执行顺序建议。 |

## 使用建议

1. 先从上面的分类表定位场景。
2. 如果是文档交付类任务，优先看 `delivery/`；如果是技术方案图片、部署图、数据模型图，优先看 `arch-diagram-style/`。
3. 如果是项目开发过程管理：
   - 先用 `project-dev-governance/` 整理需求基线、开发前材料和迭代边界。
   - 需要长期维护项目计划和状态时，用 `planning-with-files-zh/`。
   - 需要把一个目标快速拆成具体任务时，用 `planning-and-task-breakdown/`。
4. 进入具体 skill 目录阅读 `SKILL.md` 与 `references/`，确认它能解决什么问题。
5. 需要给 Codex 使用时，以具体 skill 目录为单位安装或复制。

## 项目开发类 Skill 的推荐组合

- `project-dev-governance`
  负责项目级治理，适合做需求清单、开发前材料、迭代边界和变更控制。
- `planning-with-files-zh`
  负责持续跟踪，适合做阶段计划、当前状态、下一步动作的长期维护。
- `planning-and-task-breakdown`
  负责任务拆解，适合把单次目标拆成具体可执行步骤。

建议优先顺序：

1. 先用 `project-dev-governance` 定义范围和基线。
2. 再用 `planning-and-task-breakdown` 拆当前阶段任务。
3. 最后用 `planning-with-files-zh` 持续跟踪项目推进。
