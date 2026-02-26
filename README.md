# muro-reddit

Claude Code plugin — Reddit outreach agent for [Muro](https://usemuro.com). Finds relevant wall paint/color threads and drafts warm, human-sounding replies. Uses the `humanizer` skill to strip AI patterns before showing you drafts.

## Install

### Step 1 — Install the humanizer dependency

```bash
mkdir -p ~/.claude/skills/humanizer
curl -o ~/.claude/skills/humanizer/SKILL.md https://raw.githubusercontent.com/blader/humanizer/main/SKILL.md
```

### Step 2 — Add this plugin as a marketplace

In Claude Code:

```
/plugin marketplace add YOUR_GITHUB_USERNAME/muro-reddit-plugin
```

### Step 3 — Install the plugin

```
/plugin install muro-reddit
```

### Step 4 — Initialize state directory

```bash
mkdir -p ~/.claude/reddit-agent
```

The state file (`~/.claude/reddit-agent/state.json`) is created automatically on first run.

## Usage

Start a session:

```
/muro-reddit:reddit
```

The agent will:
1. Report your current warm-up status across subreddits
2. Ask which subreddits to scan
3. Search Brave (fallback: Google) for recent threads
4. Score and filter threads by relevance
5. Draft replies, run each through the humanizer
6. Show you drafts for approval (with Reddit URL on every draft)
7. Write approved replies to `~/.claude/reddit-agent/drafts-YYYY-MM-DD.md`
8. Update state after you confirm posts

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
