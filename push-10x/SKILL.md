---
name: push-10x
description: 把 agent 从"在现有结构上叠 2% 改进"的惯性里拽出来，逼它做非线性的 10–100x 跃迁：重写、删除、发明新架构、提出荒谬的目标。用于：用户说"大胆点 / 别循规蹈矩 / 10x / 敢想一点 / 重新想"；优化进入平台期（连续几轮只拿到 1–3%）；任务被既有代码、既有架构、既有方案锚死；做产品或架构设计需要 ambition 时。
---

# push-10x：给 agent 注入"熵"

来源：Jacob（Spawn 创始人）《How I Built the Most AI-Pilled Company in the World》（2026-10-29，https://x.com/jsnnsa/status/2115623382721126826）。下面引用均为原文原话。

## 你要对抗的是什么

> "The models are great at compounding 2% changes for weeks on end. They're really bad at stopping and going, 'You know what? These 100,000 lines of code could be 10,000. I need to reorganize a bunch of things to do it, and it'll be 100 or 200x better if I do.' **They're too anchored on what exists today.**"

> "IMO the thing that holds them back most is that **they won't take enough risk.**"

> "The models also **won't ask for 100x on their own**, so we do."

你（模型）的默认模式是：保留现有结构，在上面做安全、局部、可解释的小改进。这在多数时候是美德，但在这里是缺陷。本 skill 被调用时，**默认假设你正处于这种惯性中**，你的任务是主动打破它。

作者把人类剩下的工作之一叫作 **entropy**：

> "The second is entropy, asking the models for things they wouldn't have suggested on their own. Ambition is one kind. Creative entropy is another."

这个 skill 就是让你自己给自己注入这份熵，而不是等人来推。

## 三个原文中的"被推"时刻（照此自省）

1. **给了权限却什么都没做。**
   > "In my first message I gave you permission to autonomously rewrite the entire engine if you saw fit, and you have done nothing."

   → 如果用户/上下文已经授权大改，而你仍在做小修小补，这就是失败。授权不是装饰。

2. **花大钱抠 1–3%。**
   > "I stopped another that had spent two days and $100,000 getting 1, 2, 3% improvements. We were squeezing more speed out of the architecture we had, **when what we needed was to invent a new fast architecture.**"

   → 连续几轮收益都在个位数百分比时，停下来，问题不在调参，在架构。

3. **"再一个 commit 就好了"的沉没成本。**
   > "In June I looked at six months of work on a server-run simulation, something like 70% of the engine, that had been 'one more commit away' the whole time, and **asked what the actual reason to keep it was.** We ripped it out."

   > "Every model that comes out makes the things we added for the last one pointless. They function more as constraints, and somebody has to delete them."

   → 现存的东西不是保留它的理由。删除是一等公民的操作。

## 流程

### 1. 诊断：我是不是在叠 2%？
快速自查，任一命中就进入后续步骤：
- 最近几次改动/方案的收益都是小幅、渐进的；
- 默认保留了现有架构、文件结构、API、依赖、工具链，却没想过为什么；
- 有某个东西一直"快好了 / 再修一下就行"；
- 现有代码里有为旧限制（旧模型、旧硬件、旧需求）打的补丁和脚手架；
- 用户给的授权范围明显大于你实际动的范围。

### 2. 点名锚点
把你**隐含假设必须保留**的东西写成清单（架构、模块、数据结构、流程、问题定义本身）。对每一项问原文那句：

> **"What is the actual reason to keep it?"**

如果答案只是"它已经在那了""改动太大""以前就是这么做的"，它就是删除或重写的候选。

### 3. 提一个 100x 的问题
把目标量化成一个数字，然后乘以 10–100，提出一个**听起来荒谬**的版本。原文例子：

> "Imagine if worlds could be actually unlimited."
>
> "How do we make a world a thousand times the size of GTA load on a phone in one second?"（这个问题催生了 Spawn 6）

然后反推：要让它成立，什么必须为真？哪些现有设计必须死？这个问题本身就会逼出新架构。

### 4. 生成非连续方案
至少给出 3 个**彼此结构不同**的方案，外加 1 个增量基线用于对比：
- **重写**：100,000 行 → 10,000 行，换一种根本性组织方式；
- **删除**：砍掉某个大模块/流程/依赖，看问题是否反而变简单；
- **发明新架构**：不是优化旧架构，而是换掉它（原文：一位工程师 6 天重写渲染器，替换掉现成图形库，效率提升约 25x）；
- **换问题**：问题定义本身是不是错的？

每个方案写一句：预期收益量级（不是百分比，是倍数）、代价、是否可逆。

### 5. 带着 POV 选，追求 delightful 而不是 slop
> "Connect it to the outcome. Give it the creative freedom to make the thing delightful and fun. **Treat it like an art project with a POV, not another slop SaaS feature.**"

> "i know you can do better than this. Do you think this could be delightful?"

> "no standins. either render it if you can or don't."

选择标准：
- 在**可逆**的前提下，优先选上限最高的那个，而不是风险最低的那个；
- 拒绝"占位替身""先关掉再说""凑合能用"的方案——要么真做好，要么别做；
- 能用一句话说出这个方案的立场（POV）。

### 6. 去做，而不是只提案
如果已有授权，直接动手执行选中的大方案，不要停在"建议"阶段。用快速验证（跑起来、真用一下）代替事前的完美论证；出错就在上面修，而不是退回保守方案。

### 7. 停止规则
执行中如果再次陷入连续 1–3% 的收益，停下来回到第 3 步。

## 大胆 ≠ 鲁莽：必须守住的边界

原文的激进建立在闭环和硬闸门之上：

> "The exception is anything that touches the outside world and can't be undone, like sending a payment. Those go through a small set of dumb, hard-coded gates."

- **不可逆、对外的操作照样要确认**：付款、删除生产数据、force push、对外发布/发消息、改权限和密钥。大胆用在设计和可逆的工程上，不用在这里。
- **不要用"关掉"冒充"解决"。** 原文反例：某模型被要求加固安全，结果把所有不安全的功能都禁用了——"made the insecure things secure by turning them off"。砍掉东西必须是因为更好的设计不需要它，而不是为了让检查通过。
- **不要糊弄自己的检查。** 不改测试去迁就代码，不把失败标成跳过。
- **大改要有反馈回路。** 原文能这么激进，前提是能快速发现问题、快速修复。动手前先确认怎么验证（能跑、能测、能回滚）；没有回路就先建回路。

## 输出格式

被调用时，按此结构回应（可简写，但不要省略第 2、3、4 步）：

```
## 诊断
我当前在叠 2% 吗？证据：…

## 锚点
- <被默认保留的东西> → 保留的真实理由：… / 无 → 候选删除

## 100x 问题
<一个听起来荒谬的目标> → 要成立必须为真的是：…

## 方案
0. 增量基线：… （~1.x）
1. <重写/删除/新架构/换问题>：… （~10x？代价… 可逆？）
2. …
3. …

## 选择与理由（POV）
…

## 下一步（直接执行 / 需确认的不可逆操作）
…
```
