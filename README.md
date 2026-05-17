# Novel Finder Skill

`novel-finder` is a Codex skill for finding Chinese web novels through iterative preference discovery, keyword generation, and source-aware candidate evaluation.

The skill is designed for readers who know what they want but struggle with vague tags, repeated popular recommendations, hidden dealbreakers, or scattered official reading sources.

## What It Does

- Builds a session-level taste profile from liked books, disliked books, must-haves, dealbreakers, and freshness constraints.
- Tracks already-read and already-rejected titles so recommendations do not repeat obvious classics.
- Converts vague requests into searchable keyword groups across genre, trope, protagonist type, tone, platform, freshness, and exclusion terms.
- Prefers official or authorized sources such as 起点中文网, 晋江文学城, 番茄小说, 纵横中文网, 刺猬猫, 飞卢, 七猫, QQ阅读, 微信读书, 掌阅, 豆瓣读书, publisher pages, and author pages.
- Evaluates each candidate with match reason, likely risks, evidence quality, confidence, and a trial-reading checkpoint.
- Avoids piracy links, full-text mirrors, download sites, and paywall-bypass guidance.

## Repository Structure

```text
novel-finder/
  SKILL.md
  agents/
    openai.yaml
  references/
    novel-search-workflow.md
```

## Usage

Use the skill when asking Codex to help find novels, for example:

```text
Use $novel-finder 帮我找都市异能完本，主角成长型，剧情不要降智，后宫可以有但不要抢主线。
```

## Example Prompts

### Find a Novel from Current Taste

```text
Use $novel-finder 我想看都市网文，主角要有异能，可以有后宫，但后宫戏份不要抢主线。剧情不能太无脑，尤其反派智商和人物动机要站得住，只要完本，不要太早期。
```

### Find Something Similar

```text
Use $novel-finder 帮我找类似《诡秘之主》的小说。我喜欢神秘学、世界观揭示、伏笔回收和主角谨慎成长，但不想要克系太重，也不要主角一路无脑莽。
```

### Avoid Already-Read Classics

```text
Use $novel-finder 我想找近年完本都市异能文，但《夜的命名术》《大王饶命》《第一序列》《黄金瞳》《天王》都看过了。请优先找没那么常被推荐的，给出正版来源和试读检查点。
```

### Female-Oriented Cultivation Search

```text
Use $novel-finder 我想看女频修仙，女主事业线强，少误会，感情线可以有但不要拖主线。不要虐主、不要强行降智，最好完结。
```

### Output Shape Example

The skill should normally return something like:

```markdown
**口味画像**
- 核心需求:
- 加分项:
- 明确排除:
- 已读/已拒:
- 新鲜度要求:

**关键词组合**
| 目的 | 关键词 |
|---|---|

**候选小说**
| 优先级 | 书名 | 作者 | 候选类型 | 正版/官方来源 | 匹配理由 | 可能雷点 | 依据与置信度 | 试读检查点 |
|---|---|---|---|---|---|---|---|---|

**下一轮收窄**
1. ...
2. ...
```

For the best results, provide:

- Books you liked and why.
- Books you dropped or already read.
- Hard dealbreakers, such as 降智, 后宫, 虐主, 烂尾, 系统文, or 感情戏喧宾夺主.
- Freshness constraints, such as 2020 后, 近年完本, 不要太早期, or 经典也可以.
- Platform or status preferences, such as 起点优先, 番茄也可以, 完本 only, or 连载可追.

## Workflow

1. Clarify taste through a few focused questions.
2. Summarize the current taste profile.
3. Generate targeted search keywords.
4. Search official and review sources when available.
5. Filter candidates through the quality gate.
6. Return a table with match reason, risks, evidence, confidence, and trial checkpoints.
7. Update the profile after feedback and search again.

## Validation

Validate the skill with the system `skill-creator` validator:

```powershell
python -X utf8 C:\Users\81901\.codex\skills\.system\skill-creator\scripts\quick_validate.py novel-finder
```

Expected output:

```text
Skill is valid!
```
