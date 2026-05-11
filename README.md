# Voice Actor Income Research Skill

这是一个用于调研和估算日本声优年度收入的可复用 Skill，重点适用于：

- 日本声优年收入估算
- 声优与企划乐队 / project-live 收入拆解
- 动画、广播、live、会员订阅、角色歌、联名商品的收入建模
- 事务所抽成后个人税前收入估算
- 保守 / 基准 / 乐观三情景模型

## 文件结构

```text
voice_actor_income_research_skill/
├── SKILL.md                         # Skill 主体说明
├── README.md                        # 使用说明
├── examples/
│   └── example_prompt.md            # 调研提示词示例
└── templates/
    ├── activity_inventory.csv       # 公开活动清单模板
    ├── income_model.csv             # 收入模型模板
    └── sensitivity_analysis.csv     # 敏感性分析模板
```

## 推荐使用方式

把整个目录放入你的 agent / ChatGPT skills 目录中，例如：

```bash
~/.agents/skills/voice_actor_income_research/
```

或：

```bash
~/.codex/skills/voice_actor_income_research/
```

具体目录取决于你使用的 agent 是否读取该路径。

## 适用输入示例

```text
请你调研日本声优 <声优名> 在 <年份> 的大致年收入，单位日元。
请从人气、长期饭票、短期业务、IP 分成、演出分成、事务所分成和抽成等维度拆解。
请给出保守、基准、乐观三种情景，并说明关键假设和置信度。
```

## 输出口径

默认口径是：

> 事务所抽成后、个人所得税和社保前的个人税前收入。

不要把以下口径混用：

- 项目总流水
- 事务所收到的 gross contract value
- 声优个人税前收入
- 声优税后到手
- IP 权利方收入
- 制作委员会收益

## 方法核心

```text
公开活动量 × 行业价基 × 分账假设 × 三情景敏感性分析
```

## 必须注意

1. 声优私人合同不可见，结论只能是估算模型。
2. IP 分成默认设为 0，除非公开证据证明本人拥有权益。
3. live 通常优先按出演费估算，不直接按票房乘声优分成。
4. 会员订阅总流水不等于声优收入，需要考虑平台、制作方、事务所分账。
5. 必须明确公开事实和模型假设的边界。
6. 最终结论建议四舍五入到 10 万或 100 万日元，不要伪精确。

## 模板说明

- `activity_inventory.csv`：用于收集目标年份公开活动。
- `income_model.csv`：用于填入各收入流的保守 / 基准 / 乐观估算。
- `sensitivity_analysis.csv`：用于评估关键参数变化对最终收入的影响。

## 典型输出结构

1. 执行摘要
2. 人物与商业化画像
3. 公开活动清单
4. 收入流估算表
5. 事务所抽成后个人税前收入
6. 敏感性分析
7. 置信度与主要不确定性
