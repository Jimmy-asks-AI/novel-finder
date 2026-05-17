---
name: novel-finder
description: Help users find Chinese web novels through multi-turn preference discovery, taste profiling, keyword generation, and search-based candidate evaluation. Use when the user asks to find novels, find books similar to a known work, generate Chinese web novel search keywords, filter by likes/dislikes, avoid unwanted tropes, or refine recommendations through conversation.
---

# Novel Finder

Use this skill to help the user discover Chinese web novels by first clarifying their current reading taste, then turning that taste into searchable keyword combinations and candidate recommendations.

## Core Workflow

1. Start with preference discovery. Ask focused questions about liked and disliked works, already-read or already-rejected books, genre, protagonist, relationship dynamics, plot hooks, power system, tone, pacing, length, completion status, platform constraints, freshness constraints, favorite "爽点", and hard "毒点".
2. Build a taste profile before searching. Summarize what the user wants, what they want to avoid, what they have already read, and which preferences are uncertain.
3. Generate search keywords. Produce multiple query groups that combine genre, trope, protagonist type, tone, exclusion terms, comparison works, freshness windows, and platform filters.
4. Search or guide search. When search tools are available and the user wants candidates, search with the generated keywords and verify book title, author, official or authorized reading source, completion or update status, review signals, and whether the candidate is too obvious for this user. If search is unavailable, output copyable queries and suggested official platforms instead of inventing results.
5. Return candidates in a structured table. Include match reason, likely risks, source evidence, confidence, freshness fit, and a short trial-reading checkpoint.
6. Iterate after feedback. Treat every rejected or already-read candidate as evidence, update the taste profile, add it to the session exclusion list, adjust keywords, and search again.

## Source Rules

- Prefer official or authorized reading sources such as 起点中文网, 晋江文学城, 番茄小说, 纵横中文网, 刺猬猫, 飞卢, 七猫, QQ阅读, 微信读书, 掌阅, 豆瓣读书, publisher pages, and author pages.
- Use community sources only as discovery or review signals, not as reading-entry replacements.
- Do not provide piracy, full-text scraping, download sites, paywall bypasses, or instructions for accessing unauthorized copies.
- Do not fabricate titles, authors, platform availability, ratings, or review claims. Mark uncertain items as unverified.

## Reference

Read `references/novel-search-workflow.md` when using this skill. It contains the deep-question template, keyword dimensions, Chinese web novel platform list, search query patterns, output table schema, and source-safety rules.
