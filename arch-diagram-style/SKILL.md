---
name: ts-arch-diagram-style
description: 为南京三方一体化数字信息平台优化提升项目第三章生成或调整技术方案架构图、数据模型图、部署与运行保障图时使用。适用于沿用当前项目已定稿的标题栏、分层容器、卡片、箭头、字号与配色规则，并基于 analysis/source.md、analysis/negotiation-ref.md 和现有 output/tech-arch 图片继续出图。
---

# TS Arch Diagram Style

用于本项目第三章技术方案图片的局部风格与出图约束。优先复用现有脚本：

- `analysis/generate_arch_diagrams.py`

必要时读取：

- `references/style-rules.md`
- `references/data-model-pattern.md`
- `references/image-samples.md`

## 触发场景

- 用户要求继续调整 `3.7` 至 `3.12` 的技术方案图片
- 用户要求生成 `3.8.4 / 3.9.4 / 3.10.4 / 3.11.4` 数据模型图
- 用户要求生成或修改 `3.12` 总体部署与运行保障图
- 用户要求保持与当前 `output/tech-arch` 已定稿图片一致的风格

## 必须遵守

1. 标题栏沿用当前浅蓝顶栏、大号深蓝标题、小号灰色副标题。
2. 图内正文优先使用短句；并列项用 `、` 连接，不堆长段落。
3. 分层图优先使用“大层容器 + 卡片框”；层与层之间默认单条总箭头。
4. 卡片标题条颜色保持现有体系：
   - 蓝：平台/服务/统计
   - 绿：业务主链/能力域
   - 橙：流程、控制、部署保障
   - 紫：留痕、状态、数据模型补充
5. 数据模型图不要画成数据库 ER 明细图；用“核心实体卡片 + 关键字段 + 规则说明 + 少量关系箭头”的评审型表达。
6. `3.12` 不能直接套旧图，必须以正文 `3.12` 部署保障要点为主，再补 `3.8-3.11` 部署对象和 `3.13` 边界约束。
7. 所有文字必须完整落在显示框内；不得出现标题压正文、正文出框、正文贴边过紧、文字与箭头重叠。
8. 若图用于终稿排版，标题默认不带章节号；如 `3.7`、`3.8.1`、`3.10.4` 等前缀应移除，仅保留图名。
9. 层与层之间除非用户明确要求，否则只保留 1 条总箭头；不要为每个上层卡片分别向下画多条竖向箭头。
10. 规则说明框、状态框、留痕框是最容易出排版问题的区域，优先保证其高度、内边距与层容器底边留白。

## 出图流程

1. 先从 `analysis/source.md` 找到对应章节正文。
2. 若涉及三期功能或业务边界，再读 `analysis/negotiation-ref.md`。
3. 若是风格延续，参考现有：
   - 先看 `references/image-samples.md`
   - 外部参考图放在 `assets/best-reference-images/`
   - 当前项目终版图放在 `assets/final-images/`
   - 其中 `assets/final-images/3.8.1-pecms-capability-v4.png` 是当前最重要的版式基准图
4. 优先修改 `analysis/generate_arch_diagrams.py`，不要手工拼图片。
5. 导出后逐张检查：
   - 文字是否都在框内
   - 箭头是否压字
   - 分层与章节正文是否一致
   - 标题是否需要去掉章节号
   - 层间是否误用了多条总箭头
   - 规则说明框、底部留痕框是否有贴边或越框

## 快速定位

- 章节检索：
  - `Select-String -Path analysis\source.md -Pattern '^### 3\.(8|9|10|11|12)|^#### 3\.(8|9|10|11)\.4'`
- 输出目录：
  - `output/tech-arch`
- skill 内图片参考：
  - `assets/best-reference-images`
  - `assets/final-images`
