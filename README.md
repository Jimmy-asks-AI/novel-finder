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
