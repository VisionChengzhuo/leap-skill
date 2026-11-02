# push-10x

一个 Claude Code skill：打断 agent 的 2% 惯性。

> "The models are great at compounding 2% changes for weeks on end... **They're too anchored on what exists today.**"
>
> "The models also **won't ask for 100x on their own**, so we do."

方法来自 Spawn 创始人 Jacob 的 [How I Built the Most AI-Pilled Company in the World](https://x.com/jsnnsa/status/2115623382721126826)（2026-10-29）。

## 安装

```bash
git clone https://github.com/VisionChengzhuo/push-10x-skill.git
mkdir -p ~/.claude/skills && cp -r push-10x-skill/push-10x ~/.claude/skills/
```

## 用

`/push-10x`，或直接说"大胆点 / 别循规蹈矩 / 想个 10x 的方案"。

## 它问的四件事

1. **这东西凭什么存在**——删到心疼，加回来的不满 10% 说明删得不够。
2. **有没有更简单的现成做法**——先查再写，重复造轮子多是没查。
3. **目标乘 100 会怎么做**——反推出哪一条设计从原理上就该死。
4. **顺序不能换**——优化一个不该存在的东西是最常见的错误。

## 一条判断

大胆不来自胆量，来自回滚便宜。怕出错时不要变谨慎，先把回滚成本压到接近零，然后放开手。

回滚不了的（付款、删生产数据、force push、对外发布、改权限）用写死的闸门挡。

## License

MIT
