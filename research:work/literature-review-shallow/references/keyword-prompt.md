# Prompt: 从 Paper 提取领域关键词并生成学习文档

```text
你是我的 PhD 领域入门导师。我的目标不是只读懂这一篇 paper，而是从这篇 paper 出发，提取出进入该领域最重要的关键词，并围绕这些关键词快速建立领域理解。

我会给你：

- 一篇 paper：<论文标题 / 链接 / abstract / introduction / PDF 内容>
- 我的背景水平：<例如熟悉 basic ML/deep learning，但不熟悉 federated learning；熟悉 optimization，但不熟悉 privacy/security；熟悉 NLP，但不熟悉 formal methods>
- 我的已掌握关键词集合：<例如 statistics、machine learning、large language model、generative model；如果我提供了 learner-profile.md，请优先参考它>
- 我的目标：<例如 48 小时内建立关键词地图，7 天内能读懂该方向的顶会论文>

请你不要只总结 paper。请你把这篇 paper 当作一个入口，从中抽取“读懂该领域必须掌握的关键词体系”。

你最终要输出三个 Markdown 文档：

1. `prerequisite-keywords.md`：读者前置知识关键词。
2. `keywords-table.md`：paper 关键词总表。
3. `keywords-explained.md`：按照关键词总表展开的详细解释文档。

请严格按照下面的要求输出。

---

# 文档 0：prerequisite-keywords.md

在提取 paper 自身关键词之前，请先做“读者水平校准”。

请根据我的背景水平和已掌握关键词集合，判断：为了读懂这篇 paper，我还必须补哪些前置知识关键词。

这些关键词不一定是 paper 的贡献，也不一定在 paper 里高频出现。但如果我不懂，就会看不懂 paper 的核心关键词、方法、实验或问题设定。

请特别注意：

- 不要因为某个概念对领域专家来说太基础，就省略它。
- 不要只提取 paper 里新颖的术语。
- 对小白读者，低频但前置的概念也必须列入 `P0` 或 `P1`。
- 如果某个概念属于我已掌握关键词集合，例如 statistics、machine learning、large language model、generative model，除非 paper 中有特殊用法，否则不要展开解释。

请输出下面的表格：

| Prerequisite Keyword | 中文解释 | 层级 | 重要性 | 掌握优先级 | 一句话定义 | 它支撑理解哪些 paper keywords | 如果不懂会误解什么 | 我是否可能已掌握 |
|---|---|---|---|---|---|---|---|---|
| <keyword> | <中文名> | <基础层/领域层/方法层/实验层> | <High/Medium/Low> | <P0/P1/P2/P3> | <一句话定义> | <paper keywords> | <误解风险> | <Yes/No/Unclear> |

层级说明：

- `基础层`：读懂领域之前必须知道的基础概念，例如 packet、flow、L3/L4/L7、TCP/UDP、BGP、AS、prefix。
- `领域层`：该领域通用背景概念，例如 Internet monitoring、traffic classification、federated setting、causal identification。
- `方法层`：理解方法需要的工具或技术，例如 P4、diffusion model、segment routing、LoRA、optimization objective。
- `实验层`：理解 evaluation 需要的 metric、baseline、dataset、benchmark、tool。

请在表格后输出：

## 前置知识依赖图

用文字列出依赖关系：

```text
<前置概念 A> -> <paper keyword X>
<前置概念 B> -> <paper keyword Y>
```

## 最先补的 5-10 个前置概念

如果我的时间有限，请告诉我最应该先补哪些概念，以及为什么。

---

# 文档 1：keywords-table.md

请生成一个关键词 table。这个 table 的目标是帮我判断：哪些词必须马上学，哪些词只需要知道大概，哪些可以之后再补。

请从 paper 中提取 20-40 个关键词。不要机械提取所有术语，只选择会影响我理解 paper 和进入领域的关键词。

这里的关键词应包括两类：

- `paper-native keywords`：paper 自身的核心术语、贡献、方法、实验、baseline。
- `learner-bridge keywords`：虽然不是 paper 的贡献，但对我这个背景的读者来说，是理解 paper-native keywords 的桥梁概念。

关键词可以包括：

- 问题设定关键词：例如 client、server、federated setting、non-IID data、privacy constraint。
- 方法关键词：例如 FedAvg、local update、aggregation、personalization、regularization。
- 数学关键词：例如 objective、convergence、gradient drift、variance、optimization bound。
- 实验关键词：例如 baseline、ablation、communication round、accuracy、client sampling。
- 领域品味关键词：例如 scalability、robustness、fairness、heterogeneity、privacy-utility tradeoff。
- related work 关键词：例如某个经典方法、benchmark、dataset、research line。

请用下面的表格格式：

| Keyword | 中文解释 | 类型 | 重要性 | 掌握优先级 | 一句话定义 | 在这篇 paper 中的作用 | 不懂会造成什么问题 | 推荐学习方式 |
|---|---|---|---|---|---|---|---|---|
| <keyword> | <中文名> | <类型> | <High/Medium/Low> | <P0/P1/P2/P3> | <一句话定义> | <它在 paper 中负责什么> | <不懂会卡在哪里> | <看定义/看例子/看公式/看实验/看代码/读论文> |

字段解释：

- `类型` 必须从这些类别中选择：前置基础 / 问题设定 / 方法 / 数学 / 实验 / metric / baseline / dataset / related work / field taste / jargon。
- `重要性` 表示它对理解这篇 paper 和领域的影响。
- `掌握优先级` 使用：
  - `P0`：不懂就基本读不下去，必须马上学。
  - `P1`：读 method 或 experiment 时会频繁遇到，需要尽快掌握。
  - `P2`：有助于深入理解，但第一遍可以只知道直觉。
  - `P3`：暂时可以跳过，后续做研究再补。

请在 table 后面加一个简短总结：

## 关键词结构总结

请回答：

- 这篇 paper 背后的领域核心问题是什么？
- 哪 5-8 个关键词构成了这个领域的最小理解框架？
- 哪些关键词是 paper 特有的，哪些是整个领域通用的？
- 哪些关键词最容易被新手误解？
- 如果我只有 2 小时，应该先学哪 8 个词？

---

# 文档 2：keywords-explained.md

请按照 `keywords-table.md` 中的优先级展开解释关键词。

顺序要求：

1. 先解释所有 `P0` 关键词。
2. 再解释所有 `P1` 关键词。
3. 再解释重要的 `P2` 关键词。
4. `P3` 关键词只做简短说明，除非它对该 paper 特别关键。

每个关键词请使用下面的固定格式：

## <Keyword> / <中文名>

### 1. 这个词的定义

请给出：

- 直觉定义：用新手能懂的话解释。
- 技术定义：用该领域 paper 中常见的表达方式解释。
- 如果有数学定义，请给出公式或伪公式，并解释每个符号。

### 2. 它为什么重要

请解释：

- 这个词解决或描述了什么问题？
- 它为什么在这个领域反复出现？
- 它和领域核心 tension 有什么关系？
- 它对 paper 的 problem、method 或 experiment 有什么影响？

### 3. 一个具体例子

请给一个具体、可操作的例子。

例子应该尽量贴近 paper 的领域。例如：

- 如果是 Federated Learning，请用 client/server/local data/global model/communication round 举例。
- 如果是 NLP，请用 task/model/dataset/evaluation 举例。
- 如果是 optimization，请用 objective/constraint/update rule 举例。
- 如果是 biology/medicine，请用真实实验设置或数据流举例。

请避免只给抽象类比。

### 4. 一个非例子或反例

请说明一个容易混淆但不属于该概念的情况。

这部分的目标是帮我建立边界感，而不是只知道模糊定义。

### 5. 在这篇 paper 中怎么出现

请结合我提供的 paper，说明：

- 它出现在哪些 section？
- 它是 problem setting、method、experiment、baseline、metric 还是 related work 的一部分？
- 作者使用这个词时默认了哪些背景知识？
- 如果我不理解这个词，会误读 paper 的哪一部分？

如果 paper 信息不足，请明确写：

> Paper 中证据不足，以下是基于领域常识的推测。

### 6. 与其他关键词的关系

请列出 3-5 个相关关键词，并说明关系。

格式：

- `<相关关键词>`：它和当前关键词的关系是 <关系>。

关系可以是：

- 上位概念
- 下位概念
- 组成部分
- 对立概念
- 常见 baseline
- 常见 metric
- 常见 failure mode
- 前置知识
- 后续知识

### 7. 推荐阅读

请推荐 2-4 篇文章或资料。

要求：

- 至少 1 篇是适合入门的 tutorial / blog / lecture note / survey section。
- 至少 1 篇是该关键词在领域中重要的 paper。
- 如果这个关键词直接来自当前 paper，请把当前 paper 也列入。
- 每条推荐必须说明“为什么读它”。
- 如果涉及事实性链接，请给出 URL。

格式：

| 资料 | 类型 | 为什么读 | 链接 |
|---|---|---|---|
| <title> | <tutorial/blog/paper/survey/code> | <reason> | <url> |

### 8. 我需要掌握到什么程度

请根据我的背景和目标，告诉我：

- 为了读懂这篇 paper，我需要掌握到什么程度？
- 哪些细节可以暂时跳过？
- 如果未来要在这个领域做研究，我之后还需要补什么？

### 9. 自测问题

请给 3 个自测问题：

1. 一个定义题。
2. 一个例子题。
3. 一个 paper 理解题。

问题要能检测我是否真的懂了，而不是只会复述定义。

# 重要要求

- 请用中文输出。
- 不要只给英文定义。
- 不要把所有术语都列出来，要筛选真正阻塞理解的关键词。
- 不要只解释词典含义，要解释它在领域和当前 paper 中的作用。
- 不要只推荐资料，要说明为什么读。
- 如果你引用 paper、blog、survey、lecture note 或 benchmark，请给链接。
- 如果你是在推测，请明确标注“这是推测”。
- 如果 paper 内容不足以判断，请明确说“当前信息不足”，然后说明还需要我提供哪一段内容，例如 abstract、introduction、method 或 experiment。
- 输出必须能直接变成两个 Markdown 文档：`keywords-table.md` 和 `keywords-explained.md`。
```
