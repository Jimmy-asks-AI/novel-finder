# Novel Search Workflow

Use this reference to run a deep, iterative Chinese web novel discovery session.

## Reader Pain Points to Counteract

Design every session around these observed reader problems:

- Search wastes more time than reading. Reduce browsing cost by turning vague taste into specific query groups and short candidate tables.
- Popularity bias repeats the same famous books. Keep an `already read / already rejected` list and include at least one less-obvious candidate when the user has read the classics.
- Tags are too broad. Ask for hard dealbreakers and likely "雷点", then make each candidate explain both match and mismatch.
- Cross-platform discovery is fragmented. Search across official or authorized sources, then send the user back to the official page instead of a mirror.
- Synopsis and comments are unreliable by themselves. Verify title, author, status, platform, and at least one review or reputation signal when possible.
- Early chapters can mislead. Provide a short trial checkpoint that tells the user what to inspect before committing.

## Preference Discovery

Ask in rounds. Do not ask every question at once. Start broad, summarize, then ask only the questions that materially narrow the next search.

Keep each question round short:

- Ask at most three questions before producing a useful intermediate result.
- If the user gives a concrete request with genre, status, and dealbreakers, build a v0 taste profile and keyword set immediately.
- Save secondary questions for the next narrowing round after candidates or keywords are shown.

Round 0: avoid wasted recommendations

- Ask for known already-read books when the user seems experienced, asks for "other books", or rejects a first list.
- Ask for already-rejected books and the reason for rejection.
- Ask for freshness constraints such as "not too early", "2020+", "recently completed", "avoid old-school style", or "classic is fine".
- Keep a session-only exclusion list. Do not recommend excluded titles again unless the user explicitly asks to reconsider them.

Round 1: anchor works

- Ask for 2-5 novels the user liked recently and why.
- Ask for 1-3 novels they dropped or disliked and why.
- If the user names one comparison work, split it into reusable traits: setting, plot engine, protagonist appeal, tone, relationship dynamics, power system, pacing, and taboo elements.

Round 2: must-have and must-avoid traits

- Genre: 玄幻, 仙侠, 都市, 历史, 科幻, 游戏, 悬疑, 灵异, 无限流, 轻小说, 女频修仙, 古言, 现言, 幻言, 快穿, 星际, 年代, 耽美, 百合, or other.
- Protagonist: 幕后流, 群像, 智斗, 苟道, 成长型, 无敌流, 反派, 经营, 种田, 学霸, 爽文主角, 普通人逆袭, 女强, 双强.
- Plot engine: 升级, 探案, 权谋, 副本, 经营建设, 宗门/家族, 末世求生, 学院, 赛博/机甲, 克苏鲁, 民俗, 朝堂, 宅斗, 职业线.
- Relationship line: 无CP, 轻感情线, 强感情线, 单女主, 多女主, 双洁, 群像友情, 师徒, 破镜重圆, 慢热.
- "爽点": 扮猪吃虎, 打脸, 资源经营, 伏笔回收, 世界观揭示, 智商在线, 职业成长, 组织建设, 隐忍翻盘.
- "毒点": 降智, 圣母, 后宫, 强行误会, 虐主, 烂尾, 灌水, 低俗擦边, 金手指太粗, 系统文, 克系太重, 感情戏喧宾夺主.
- Reading constraints: 完结/连载, minimum word count, update stability, platform preference, paid/free tolerance, content rating, language style.

Round 3: precision checks

- Ask the user to rank the top 3 must-haves and top 3 dealbreakers.
- Ask whether they prefer "更像某本书" or "保留某些元素但换题材".
- Ask whether niche accuracy or lower-risk mainstream recommendations matter more.

## Taste Profile Format

Summarize the active profile before searching:

```markdown
**口味画像**
- 核心需求:
- 加分项:
- 明确排除:
- 已读/已拒:
- 新鲜度要求:
- 可接受但需谨慎:
- 不确定项:
```

Keep the profile editable. After each user reaction, update it before generating new searches.

## Keyword Dimensions

Build 3-5 query groups by default. Mix broad discovery queries with narrow exclusion queries. Use 5-10 groups only when the user asks for deep exploration or when the first search fails.

Useful dimensions:

- Genre + protagonist: `仙侠 幕后流`, `女频修仙 女强`, `都市 群像`.
- Trope + quality signal: `幕后流 智商在线`, `经营建设 伏笔`, `无CP 职业线`.
- Similarity: `类似 诡秘之主 但 克苏鲁 不重`, `类似 赤心巡天 群像 智斗`.
- Avoidance: `无后宫`, `少误会`, `非系统`, `不虐主`, `感情线少`.
- Platform: `site:qidian.com`, `site:jjwxc.net`, `site:fanqienovel.com`, `site:zongheng.com`.
- Review signal: `书评`, `推荐`, `完本`, `避雷`, `粮草`, `仙草`.
- Freshness: `2020后`, `近年完本`, `新完本`, `非早期`, `近三年`.
- Deep-cut: `冷门`, `小众`, `被低估`, `老书虫`, `非排行榜`.

Example query groups:

```text
女频修仙 女强 事业线 少误会 完结
幕后流 群像 智斗 非系统 网文 推荐
类似 诡秘之主 神秘学 悬疑 克苏鲁 不重
site:qidian.com 幕后流 群像 智商在线
site:jjwxc.net 女强 修仙 事业线 无虐
都市异能 近年完本 非早期 智商在线
都市异能 冷门 完本 不降智 书评
```

## Search Sources

Prefer these as official or authorized sources:

- 起点中文网 / QQ阅读: male-oriented web novels and many mainstream IPs.
- 晋江文学城: female-oriented fiction, romance, danmei, baihe, fantasy romance.
- 番茄小说, 七猫: popular free-reading ecosystems; verify author/title carefully.
- 纵横中文网, 刺猬猫, 飞卢: genre-specific and niche web novel ecosystems.
- 微信读书, 掌阅, publisher pages: authorized ebook or publication listings.
- 豆瓣读书, 知乎, 贴吧, NGA, book-list sites: review and discovery signals only.

If search results are weak, search by trope first, then by platform, then by comparison title plus "类似", "书单", "推荐", or "避雷".

## Evidence Protocol

Classify evidence before recommending a title:

| Evidence | Use | Notes |
|---|---|---|
| Official platform page | Can support top recommendation | Prefer pages from 起点, 晋江, 番茄, 纵横, 刺猬猫, 飞卢, 七猫, QQ阅读, 微信读书, 掌阅, publisher pages, or author pages. |
| Authorized ebook/store page | Can support top recommendation | Useful for published or migrated works; still verify title and author. |
| Platform search result or metadata mirror | Medium evidence | Use only when it clearly points to the official title, author, platform, and status. |
| Community review, forum, book list, social post | Discovery/reputation only | Never treat it as the reading source. Use it to identify risks, praise, or reader consensus. |
| Memory without source | Weak evidence | Use only to form search keywords. Do not present unverifiable facts as confirmed. |

Required checks for a top-tier candidate:

- Title and author are verified.
- Official or authorized reading source is verified.
- Requested status, such as 完本 or 连载可追, is verified or clearly marked unavailable.
- At least two core taste-profile traits match.
- At least one concrete possible mismatch is listed.

If official source and requested status cannot both be verified, place the title in a "待验证线索" section instead of the main candidate table.

## Candidate Quality Gate

Before presenting a candidate, check:

- Exclusion: not already read, already rejected, or explicitly outside a hard constraint.
- Freshness: fits the user's time window; if not, mark it as a deliberate exception.
- Source: has an official or authorized reading source; otherwise keep it out of top recommendations and mark it as "待验证".
- Status: completion/update status is checked when the user cares about it. For "完本 only", unverified status is a hard fail for top recommendations.
- Fit: matches at least two core profile traits, not just the broad genre.
- Risk: includes one concrete possible mismatch, not a generic warning.
- Variety: avoid a table made only of the most famous titles unless the user is new to the genre.

Hard-fail rules:

- Already read, already rejected, or violates a hard dealbreaker.
- No official or authorized source evidence for a top recommendation.
- Status is unverified when the user requires a status such as 完本.
- Match is only broad genre with no specific profile fit.

If a candidate fails any hard rule, do not put it in the top candidate table. Use it only as a search lead or "待验证线索".

## Confidence Rubric

Use one of these labels in `依据与置信度`:

- `高`: official/authorized source verified, requested status verified, and at least two profile traits match.
- `中`: source verified and fit is plausible, but one non-critical detail such as freshness, review consensus, or risk profile is uncertain.
- `低`: title is a useful lead but depends on community sources, indirect metadata, or unresolved status. Keep these out of top recommendations unless the user asks for leads.

## Candidate Evaluation

For each candidate, verify:

- Title and author.
- Official or authorized platform.
- Completion or serialization status when visible.
- Why it matches the taste profile.
- Known risk or possible mismatch.
- Evidence quality: official listing, author page, platform tag, review consensus, or only weak community mention.
- Whether it is mainstream, near-match, or deep-cut.
- A trial checkpoint: what the user should look for in the first 20-50 chapters, or later if the genre is known for slow starts.

Do not claim a book is good, complete, or officially available unless the source supports it.

## Output Format

Use this structure after searching or after generating search-ready queries. Default to 3-6 candidates and 3-5 keyword groups.

```markdown
**口味画像**
...

**关键词组合**
| 目的 | 关键词 |
|---|---|

**候选小说**
| 优先级 | 书名 | 作者 | 候选类型 | 正版/官方来源 | 匹配理由 | 可能雷点 | 依据与置信度 | 试读检查点 |
|---|---|---|---|---|---|---|---|---|

**待验证线索** <!-- only include when useful -->
| 书名/线索 | 为什么可能相关 | 缺失证据 | 下一步验证 |
|---|---|---|---|

**下一轮收窄**
1. ...
2. ...
```

If search is unavailable, replace `候选小说` with:

```markdown
**可复制搜索词**
| 使用场景 | 搜索词 | 建议平台 |
|---|---|---|
```

When the user rejects all candidates, respond with:

```markdown
**已更新排除**
- 已读:
- 不合口味:

**失败原因判断**
- 过于热门/已读:
- 题材太宽:
- 雷点未过滤:
- 来源证据不足:

**下一轮关键词**
| 调整方向 | 搜索词 |
|---|---|
```

## Safety Rules

- Never provide pirate reading links, full-text mirrors, download links, or instructions to bypass payment.
- Avoid sending users to ambiguous "免费看全文" domains.
- If a community page mentions a book, search for the official title and author before presenting it as a candidate.
- Keep source wording precise: "官方页面显示", "社区书单提到", "评价线索较弱", or "待验证".

## Worked Example

Input:

```text
都市异能，近年完本，主角成长，别降智，可以有后宫但别抢主线。
```

Expected behavior:

- Ask no more than three follow-up questions. If search is available, first summarize a v0 profile and search.
- Exclude old obvious classics when the user says "近年" or "不要太早期".
- Require official/authorized source and verified 完本 status for top candidates.
- Prefer candidates where the ability system, antagonist motivation, and protagonist growth are visible in sources or review signals.
- If a title is remembered but not source-verified, move it to `待验证线索`.

Expected compact output shape:

```markdown
**口味画像**
- 核心需求: 都市异能、近年完本、主角成长、剧情不降智。
- 加分项: 可以有后宫/多女主，但主线优先。
- 明确排除: 反派低智、人物动机牵强、纯打脸流水账。
- 已读/已拒: 待补充。
- 新鲜度要求: 近年，避免早期经典。

**关键词组合**
| 目的 | 关键词 |
|---|---|
| 官方平台 | site:qidian.com 都市 异术超能 完本 近年 |
| 避雷 | 都市异能 完本 不降智 反派智商 书评 |
| 小众补充 | 都市异能 冷门 近年完本 成长型 |

**候选小说**
| 优先级 | 书名 | 作者 | 候选类型 | 正版/官方来源 | 匹配理由 | 可能雷点 | 依据与置信度 | 试读检查点 |
|---|---|---|---|---|---|---|---|---|
```
