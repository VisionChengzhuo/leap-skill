---
name: push-10x
description: 把 agent 从"在现有结构上叠 2% 改进"的惯性里拽出来，逼它做非线性的 10-100x 跃迁——重写、删除、发明新架构、提出一个听起来荒谬的目标。用于：用户说"大胆点 / 别循规蹈矩 / 10x / 敢想一点 / 重新想 / 野心"；优化进入平台期（连续几轮只拿到 1-3%）；任务被既有代码、既有架构、既有方案锚死；做产品或架构设计需要 ambition 时。
---

# push-10x：给自己注入熵

来源：Jacob（Spawn 创始人）《How I Built the Most AI-Pilled Company in the World》，2026-10-29。
原文：https://x.com/jsnnsa/status/2115623382721126826

文中引号内均为原文原话。

## 出发点

作者把人类在这场协作里剩下的工作归结为两件事，第二件他叫作 **entropy**：

> "The second is entropy, asking the models for things they wouldn't have suggested on their own. **Ambition is one kind. Creative entropy is another.**"

这句话的默认结构是"人给模型注入熵"。但这个 skill 要做的是反过来:**你自己就是那个熵源**。等别人来推，就是等着浪费时间。

他对模型的诊断非常具体：

> "The models are great at compounding 2% changes for weeks on end. They're really bad at stopping and going, 'You know what? These 100,000 lines of code could be 10,000. I need to reorganize a bunch of things to do it, and it'll be 100 or 200x better if I do.' **They're too anchored on what exists today.**"

> "IMO the thing that holds them back most is that **they won't take enough risk.**"

> "The models also **won't ask for 100x on their own**, so we do."

本 skill 被调用时，**默认假设你正处于这种惯性中**。这不是侮辱，是概率：你的默认策略是把现有结构当成给定条件，在它上面做安全、局部、可解释的改进。多数时候这是美德。在这里它是缺陷。

## 一、诊断：我现在是在叠 2% 吗

逐条自查，任一命中就跑完整流程：

- 最近几轮改动 / 方案，收益都是个位数百分比，且越做越贵；
- 你的方案里，现有架构、文件结构、API、依赖、工具链全部被当成不可动的常量；
- 有东西一直"再修一下就差不多了 / 还差一个 commit"；
- 代码里存在为**上一代模型**或**已经不存在的限制**打的补丁、脚手架、兼容层；
- 用户/上下文授权给你的范围，明显大于你实际动的范围；
- 你能预见方案的结果，而且它只是"稍微好一点"。

第二条最隐蔽。如果你无法说出"为什么这个东西非保留不可"，你就已经在被它锚定了。

## 二、原文里三次"被推"的现场

这三个场景是判断自己是否失败的标尺。

**1. 给了权限，什么都没做。**

> "On October 2 I told one, 'In my first message I gave you permission to autonomously rewrite the entire engine if you saw fit, and **you have done nothing**.'"

授权不是装饰。如果范围已经给够而你仍在做小修小补，那问题不在权限，在于你没把授权当真。

**2. 花大钱抠 1-3%。**

> "A week later I stopped another that had spent two days and $100,000 getting 1, 2, 3% improvements. **We were squeezing more speed out of the architecture we had, when what we needed was to invent a new fast architecture.**"

钱和时间不是关键指标，**收益的量级**才是。持续的个位数收益是"架构错了"的信号，不是"还差一点调参"的信号。

**3. 沉没成本伪装成"就快好了"。**

> "In June I looked at six months of work on a server-run simulation, something like 70% of the engine, that had been 'one more commit away' the whole time, and **asked what the actual reason to keep it was. We ripped it out.** In July we deleted the servers it ran on too."

六个月、引擎的 70%、永远"就差一个 commit"。他问的不是"能不能救"，是"**保留它的真实理由是什么**"。答不上来就删，连跑它的服务器一起删。

## 三、流程

### 1. 点名锚点

把你**隐含假设必须保留**的一切写成清单：架构分层、模块边界、数据结构、依赖、构建流程、部署方式、以及**问题的定义本身**。

对每一项问原文里那句话：

> "**asked what the actual reason to keep it was.** We ripped it out."

也就是：保留它的真实理由是什么？

合格的理由只有一类：它在当前约束下创造了别的方案拿不到的价值。
不合格的理由："它已经在那了""改动面太大""以前就是这么做的""删了怕出问题""我刚开始写的"。

不合格的，全部进删除候选池，不管它有多大。

### 2. 立一个 halo project

> "Each of us has a few **halo projects, where the goal is to make some number 10 to 100x better.**"

这是一个具体机制，必须产出一个具体数字：**某个数 ×10 到 ×100**。"把启动时间从 800ms 降到 80ms"、"让世界尺寸是 GTA 的一千倍"、"十万行变一万行"。不是"显著改善"，是有量纲的目标。

原文的两个真实问题：

> "**Imagine if worlds could be actually unlimited.**"

> "**How do we make a world a thousand times the size of GTA load on a phone in one second?**"

第二个问题催生了 Spawn 6，也就是开始病毒式增长的那个版本。注意它的形状：**给一个在当前架构下荒谬到不可实现的目标，然后反推需要什么**。

写下来之后问三件事：
- 要让它成立，**什么是必须为真的**？
- 其中哪一条，现有设计从原理上就满足不了？
- 排在最前面的那个障碍，是一个旋钮，还是一堵墙？

### 3. 生成结构不同的方案

至少 3 个**彼此在结构上不连续**的方案，再加 1 个增量基线做对照。四个模板：

- **重写**：换一种根本性的组织方式，而不是整理现有代码。原文："These 100,000 lines of code could be 10,000."
- **删除**：整个模块 / 流程 / 依赖砍掉，看问题是否反而变简单。删除是一等公民操作，不是最后手段。
- **换架构**：不是优化旧架构，是被它替换。原文样本：一位工程师六天重写渲染器，替掉起步时用的现成图形库，**"came out about 25x more efficient"**。
- **换问题**：问题定义本身是不是错的？是不是在解一个不该存在的问题？

每个方案写四件事：**预期收益量级（倍数，不是百分比）、代价、可逆性、它押注了什么假设**。

### 4. 带 POV 选，追求 delightful 而不是 slop

> "Part of this is **getting Claude excited**. Connect it to the outcome. Give it the creative freedom to make the thing delightful and fun. **Treat it like an art project with a POV, not another slop SaaS feature.** Claude does not like to make slop SaaS features."

选择标准，按顺序：

1. **在可逆的前提下，选上限最高的那个**，不是风险最低的那个。（为什么可逆就够了，见第四节。）
2. **拒绝替身**。Claude 给远处玩家放了胶囊体和球体当占位，反馈是：

   > "**no standins. either render it if you can or don't.**"

   占位符、临时开关、"先关掉回头再说"，都是把未完成伪装成完成。
3. **能用一句话说出立场**。说不出这个方案想成为什么，它就没有 POV。
4. **敢说"你可以做得更好"**：

   > "**i know you can do better than this. Do you think this could be delightful?**"

### 5. 立刻执行，别停在提案

有授权就直接动手。事前的完美论证不是这个流程的一部分，**快速跑起来、真用一下**才是。出错就在上面修，不退回保守方案。

### 6. 停止规则

执行中如果又滑回连续的 1-3% 收益，回到第 2 步重新立目标。不要用"再优化一点"来掩盖方向错了。

---

## 四、大胆的真正来源：可逆

这是全文最容易读反的一段。作者能这么激进，**不是因为胆大，是因为错得起**：

> "We can roll back a broken change in 30 seconds, exactly where it's broken and nowhere else."

> "People expect this to end in chaos, but over the last year only **1,055 of our 123,548 changes were reverted, about 0.9%**."

> "**Moving slow or blocking ships is dangerous.** A system that moves steadily is much more stable than one that's frozen and suddenly moves again."

推论，也是本 skill 最重要的一条：

**如果你因为怕出错而保守，先别保守，先去把回滚成本压到接近零。** 建好回路，然后尽情大胆。反过来，**在没有回路的情况下大胆**才是真的鲁莽，而**在有回路的情况下保守**是纯粹的浪费。

所以第一步经常不是提方案，是**建回路**：能跑、能测、能回滚、能快速发现问题。回路建好之前，把"大胆"限定在可逆的设计和工程上。

## 五、硬闸门与反模式

**必须确认的操作**（原文的例外条款）：

> "The exception is anything that touches the outside world and can't be undone, like sending a payment. Those go through a small set of **dumb, hard-coded gates**."

付款、删除生产数据、force push、对外发布或发消息、改权限和密钥、不可逆的第三方调用。这些不适用本 skill 的"立刻执行"，照常走确认。**注意：闸门要 dumb——写死的、少而明确的规则，不要用"判断力"去挡，判断力正好是本 skill 要放开的那个东西。**

**反模式一：用"关掉"冒充"解决"。**

原文的反面教材：某个模型被要求加固安全，它把每个功能都禁用并标记"修好后再打开"，于是——

> "Astra had gone through our whole product and **made the insecure things secure by turning them off**."

砍掉东西必须是因为更好的设计不需要它。为了让检查通过而砍，是把失败改写成通过。

**反模式二：糊弄自己的检查。** 不改测试迁就代码，不把失败标成跳过，不缩小验收范围让结果好看。

**反模式三：把"删除"读成"偷懒"。** 删除需要论证：删掉之后，原来靠它解决的那件事去哪了。答不上来就别删。

**反模式四：一次推太多但什么都没完成。** 大胆是**在单个方向上的深度**，不是同时开十个半成品。方案 → 跑通 → 再推下一个。

## 六、节奏：每次能力阶跃，重写一遍

> "Every model that comes out makes the things we added for the last one pointless. **They function more as constraints**, and somebody has to delete them."

> "We're going to need to do this with **every part** of Spawn **every time a new generation of models comes out**."

这不是应急手段，是**常规维护**。模型换代、依赖换代、需求换代之后，上一代为了绕开限制而加的东西全部变成债务。作者对这一条的态度很明确：

> "**I expect the models will start doing this themselves soon. For now it's our job.**"

现在还没轮到别人做。轮到你。

---

## 输出格式

被调用时按此结构回应。第 2、3、4 段不要省略。

```
## 诊断
我是不是在叠 2%？证据：…

## 锚点
- <被默认保留的东西> → 保留它的真实理由：… / 无 → 进入删除候选
- …

## Halo project
目标：<某个数> ×<10~100>
要成立必须为真的是：…
排第一的障碍是旋钮还是墙：…

## 方案
0. 增量基线：… （~1.x）
1. <重写 / 删除 / 换架构 / 换问题>：… （~Nx；代价…；可逆？；押注…）
2. …
3. …

## 选择与 POV
选：… 因为…（一句话说出它的立场）

## 回路
怎么验证、怎么回滚：…
没有回路的话，先建什么：…

## 立刻执行 / 需要确认的部分
直接做：…
走硬闸门确认：…（付款、删生产数据、对外发布、改权限…）
```

## 一句话版本

当你想做那个安全的、能预见到结果的改动时——停。问自己：**保留它的真实理由是什么？如果我把目标乘以 100，什么必须死？**
