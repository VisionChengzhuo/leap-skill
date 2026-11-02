# push-10x

一个 Claude Code skill：把 agent 从"在现有结构上叠 2% 改进"的惯性里拽出来，逼它做非线性的 10–100x 跃迁——重写、删除、发明新架构、提出一个听起来荒谬的目标。

灵感与引用来自 Spawn 创始人 Jacob 的文章 [How I Built the Most AI-Pilled Company in the World](https://x.com/jsnnsa/status/2115623382721126826)（2026-10-29）。

> "The models are great at compounding 2% changes for weeks on end. They're really bad at stopping and going, 'You know what? These 100,000 lines of code could be 10,000…' **They're too anchored on what exists today.**"
>
> "IMO the thing that holds them back most is that **they won't take enough risk.**"
>
> "The models also **won't ask for 100x on their own**, so we do."

作者的框架里，人类剩下的工作是 **taste** 和 **entropy**——"asking the models for things they wouldn't have suggested on their own"。这个 skill 让模型自己扮演那个熵源。

## 安装

```bash
git clone https://github.com/VisionChengzhuo/push-10x-skill.git
mkdir -p ~/.claude/skills && cp -r push-10x-skill/push-10x ~/.claude/skills/
```

## 使用

在 Claude Code 里输入 `/push-10x`（可附上当前任务），或直接说"大胆点 / 别循规蹈矩 / 想个 10x 的方案 / 敢想一点"，skill 会自动触发。

## 它做什么

1. **诊断**——判断当前是否陷入"叠 2%"模式（连续个位数收益、把现有结构当常量、"再一个 commit 就好了"）。
2. **点名锚点**——对每个被默认保留的东西问原文那句话：“asked what the actual reason to keep it was”
3. **立 halo project**——把目标锁成一个乘 10 到乘 100 的数字，然后反推"要成立必须为真的是什么"。
4. **生成结构不同的方案**——重写、删除、换架构、换问题，外加一个增量基线做对照。
5. **带 POV 选**——在可逆的前提下选上限最高的，拒绝占位和替身。
6. **立刻执行**，收益回落到 1–3% 时停下重来。

## 核心主张：大胆来自可逆，不是来自胆量

原文里最容易被读反的一段：Spawn 能这么激进，不是因为他们胆大，是因为他们回滚一个坏改动只要 30 秒，全年 12 万次改动只有 0.9% 被回滚。

所以顺序是：**先建回路，再大胆**。没有回路时大胆是鲁莽，有回路时保守是浪费。

## 边界

- 不可逆、对外的操作（付款、删生产数据、force push、对外发布、改权限和密钥）照常确认。原文的说法是走 "a small set of dumb, hard-coded gates"——写死的规则，而不是用判断力去挡。
- 不允许用"把功能关掉"冒充"解决问题"。原文反例：某模型被要求加固安全，结果把所有功能都禁用了。
- 不允许糊弄检查：不改测试迁就代码，不把失败标成跳过。

## License

MIT
