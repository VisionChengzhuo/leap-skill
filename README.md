# push-10x

一个 Claude Code skill：把 agent 从"在现有结构上叠 2% 改进"的惯性里拽出来，逼它做非线性的 10–100x 跃迁——重写、删除、发明新架构、提出荒谬的目标。

灵感与引用来自 Spawn 创始人 Jacob 的文章 [How I Built the Most AI-Pilled Company in the World](https://x.com/jsnnsa/status/2115623382721126826)：

> "The models are great at compounding 2% changes for weeks on end. They're really bad at stopping and going, 'These 100,000 lines of code could be 10,000…' They're too anchored on what exists today."
>
> "The models also won't ask for 100x on their own, so we do."

## 安装

```bash
git clone https://github.com/VisionChengzhuo/push-10x-skill.git
mkdir -p ~/.claude/skills && cp -r push-10x-skill/push-10x ~/.claude/skills/
```

## 使用

在 Claude Code 里输入 `/push-10x`（可附上当前任务），或者直接说"大胆点 / 别循规蹈矩 / 想个 10x 的方案"，skill 会自动触发。

流程：诊断是否在叠 2% → 点名锚点（"What is the actual reason to keep it?"）→ 提一个 100x 问题 → 生成结构不同的非连续方案 → 带 POV 选择 → 直接执行 → 收益回落到 1–3% 时停下重来。

边界：不可逆、对外的操作（付款、删生产数据、force push、对外发布）仍需确认；不允许用"把功能关掉"冒充"解决问题"，不允许糊弄检查。

## License

MIT
