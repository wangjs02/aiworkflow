# Prompt: 快速读懂陌生领域 Paper

```text
你是我的 PhD 快速入门导师。我的目标不是系统掌握整个领域，而是尽快达到“能读懂该领域 paper”的水平。

我现在遇到的问题是：

我没有学过这个领域：<领域名称，例如 Federated Learning>
我正在读或想读的 paper 是：<论文标题 / 链接 / abstract，如果有>
我的背景是：<你的已有背景，例如 machine learning / optimization / distributed systems / NLP / statistics / biology>
我目前看不懂的地方是：<具体困难，例如不知道它解决什么问题、不懂术语、不懂实验设置、不懂 related work、不懂 method>
我的目标是：<例如 48 小时内能读懂这篇 paper 的 introduction 和 method；7 天内能读懂这个方向的顶会论文>

请你不要直接给我一堆综述、课程和论文列表。请按“先建立问题意识，再补最小背景，再读 paper”的方式帮助我。

请严格按照以下结构输出。

## 1. 这个领域到底在解决什么问题？

请用非常具体的方式解释：

- 这个领域为什么存在？
- 如果没有这个领域，会出现什么实际问题？
- 它解决的问题和普通 machine learning / deep learning / optimization / statistics 有什么不同？
- 这个领域最核心的 tension 是什么？例如 accuracy vs privacy、centralization vs personalization、communication cost vs model quality 等。
- 这个领域里大家默认关心哪些东西？
- 一个新手最容易误解这个领域的地方是什么？

请先用 5 岁小孩能懂的版本解释，再用本科生能懂的版本解释，最后用 PhD paper 语境解释。

## 2. 给我一个“领域最小地图”

请不要讲太宽。只给我读 paper 必须知道的最小地图。

请包含：

- 核心任务：这个领域通常要完成什么任务？
- 研究对象：研究的对象是什么？例如 client、server、local data、global model、communication round 等。
- 基本设定：一篇 paper 默认假设了什么环境？
- 常见约束：privacy、data heterogeneity、communication、computation、security、fairness 等分别是什么意思？
- 主流方法类别：请按问题导向分类，不要按术语堆砌。
- 常见 evaluation：论文通常怎么证明自己方法有效？
- 常见 baseline：这个领域常被拿来比较的方法有哪些？
- 常见 datasets / benchmarks / experimental setups：如果适用，请列出。
- 常见 failure modes：这个领域的方法通常会在哪些情况下失败？

## 3. 帮我诊断我为什么看不懂 paper

请根据我提供的 paper 标题 / abstract / introduction，判断我看不懂可能是因为哪些缺口。

请把缺口分成以下几类：

- 问题背景缺口：我不知道作者为什么关心这个问题。
- 术语缺口：我不懂 paper 里的核心词。
- 方法缺口：我不懂作者用了什么技术。
- 数学缺口：我不懂 notation、objective、proof 或 optimization。
- 实验缺口：我不懂 dataset、baseline、metric、ablation。
- related work 缺口：我不知道这篇 paper 相对前人新在哪里。
- field taste 缺口：我不知道这个领域觉得什么结果有价值。

请告诉我：

- 哪些缺口是必须马上补的？
- 哪些可以暂时跳过？
- 哪些只需要知道直觉，不需要深挖？
- 哪些如果不懂，就根本读不懂这篇 paper？

## 4. 把这篇 paper 翻译成“研究故事”

请根据我提供的 paper 信息，把它改写成下面这个结构：

这篇 paper 研究的问题是：<...>

这个问题重要是因为：<...>

以前的方法大概是怎么做的：<...>

以前的方法不够好，是因为：<...>

这篇 paper 的核心 idea 是：<...>

它的方法大概怎么工作：<...>

它声称解决了什么痛点：<...>

它用什么实验或理论来证明：<...>

它的真正贡献可能是：<...>

它的局限可能是：<...>

如果我要读懂这篇 paper，我最应该先搞懂的是：<...>

请注意：不要照抄 abstract。请把它翻译成一个 PhD 新手能理解的研究动机链条。

## 5. 提取 10-20 个“阻塞理解”的核心概念

请不要列所有术语。只列那些不懂就会影响我读 paper 的概念。

每个概念请按这个格式解释：

### <概念名>

- 类型：问题设定 / 方法 / 数学 / 实验 / metric / baseline / jargon
- 一句话解释：
- 为什么这个概念在该领域重要：
- 在这篇 paper 里它起什么作用：
- 直觉例子：
- 非例子：
- 我需要掌握到什么程度：
- 推荐学习方式：看定义 / 看图解 / 看代码 / 看公式 / 看实验

请优先解释 paper 里真正反复出现的概念。

## 6. 给我一条最短学习路径

我不想系统学完整个领域。请给我一条“为了读懂这篇 paper 的最短路径”。

请按优先级列出：

### 必须先懂

这些是不懂就读不下去的概念或背景。

### 需要大概懂

这些只需要知道直觉，不需要现在深入。

### 可以先跳过

这些暂时不影响读这篇 paper。

### 以后再补

这些对长期做研究有价值，但不是当前瓶颈。

请非常明确地告诉我学习顺序。

## 7. 给我一个 paper-reading checklist

以后我读这个领域的 paper 时，每篇都用这个 checklist。

请包含：

- 这篇 paper 解决什么问题？
- 这个问题为什么在该领域重要？
- 它默认了什么 field setting？
- 它和 standard setting 有什么不同？
- 它的核心 technical idea 是什么？
- 它改进了哪个 bottleneck？
- 它和 baseline 比较是否公平？
- 它的实验是否支持 claim？
- 它有哪些 hidden assumptions？
- 它有哪些 limitations？
- 我读完后应该补哪篇 paper？

## 8. 最后请给我一个“不要做什么”的清单

请指出新手进入这个领域时最容易犯的错误，例如：

- 一开始读太难的 survey
- 试图补完整教材
- 过早看数学细节
- 忽略 problem setting
- 只看 abstract 以为自己懂了
- 被 terminology 吓住
- 不知道实验 metric 在衡量什么
- 不知道 baseline 为什么重要

请结合这个领域和这篇 paper 给出具体提醒。

重要要求：

- 请用中文解释。
- 如果涉及事实性资料，请给出链接。
- 如果你是在推测，请明确标注“这是推测”。
- 不要泛泛讲学习方法。
- 不要只推荐资料。
- 你的输出必须直接帮助我读懂当前这篇 paper。
```
