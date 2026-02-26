# muro-reddit

Claude Code plugin — Reddit outreach agent for [Muro](https://usemuro.com). Finds relevant wall paint/color threads and drafts warm, human-sounding replies. Uses the `humanizer` skill to strip AI patterns before showing you drafts.

## Install

Two commands. That's it.

```
/plugin marketplace add mszyma/muro-reddit-plugin
/plugin install muro-reddit
```

Dependencies (humanizer skill, state directory) are installed automatically on first run.

## Usage

```
/muro-reddit:reddit
```

On first run it installs the humanizer skill automatically, then:
1. Reports your warm-up status across subreddits
2. Asks which subreddits to scan
3. Searches Brave (fallback: Google) for recent threads
4. Scores and filters threads by relevance
5. Drafts replies, runs each through the humanizer
6. Shows you drafts for approval (Reddit URL on every draft)
7. Writes approved replies to `~/.claude/reddit-agent/drafts-YYYY-MM-DD.md`
8. Updates state after you confirm posts

## Session limits

- Max 3 replies per session
- Max 1 Muro mention per session
- 8 warm-up replies required per subreddit before any Muro mention

## State files

| File | Purpose |
|------|---------|
| `~/.claude/reddit-agent/state.json` | Tracks warm-up counts, replied threads, replied users |
| `~/.claude/reddit-agent/drafts-YYYY-MM-DD.md` | Clean plain-text drafts, one file per day |

## Requirements

- Claude Code with Chrome MCP extension installed and running
- User logged into Reddit in Chrome
- `humanizer` skill installed (see Step 1)
