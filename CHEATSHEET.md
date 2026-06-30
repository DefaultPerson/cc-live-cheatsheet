# Claude Code Cheatsheet v2.1.196

> Auto-generated from [cheatsheet.json](cheatsheet.json) | [Visual version](cheatsheet.png) | [Interactive](https://defaultperson.github.io/cc-live-cheatsheet/)

## Recent Changes

- Streaming idle watchdog on by default; CLAUDE_ENABLE_STREAM_WATCHDOG=0 disables *(v2.1.196)*
- ← opens agents view (changed from ←← double press) *(v2.1.196)*
- Org/Role default models appear in /model when admins set one *(v2.1.196)*
- Remote Control disabled for non-Anthropic ANTHROPIC_BASE_URL *(v2.1.196)*
- Background sessions survive process stop/restart/update *(v2.1.196)*
- claude mcp list won't spawn untrusted .mcp.json servers *(v2.1.196)*

---

## ⌨️ Keyboard Shortcuts

### General Controls

| Key | Description |
|-----|-------------|
| `Ctrl C` | Cancel input/generation |
| `Ctrl D` | Exit session |
| `Ctrl L` | Clear screen + force full redraw |
| `Ctrl O` | Toggle verbose transcript |
| `Ctrl R` | Reverse search history |
| `Ctrl G` | Open prompt in editor |
| `Ctrl B` | Background running task |
| `Ctrl T` | Toggle task list |
| `Ctrl+X Ctrl+K` | Kill background agents |
| `Esc Esc` | Rewind / undo |
| `←` | Open agents view **NEW** |
| `{ / }` | Jump between user prompts (transcript view) |
| `?` | Show keyboard shortcuts (transcript view) |

### Mode Switching

| Key | Description |
|-----|-------------|
| `Shift Tab` | Cycle permission modes |
| `Alt P` | Switch model |
| `Alt T` | Toggle thinking |

### Input

| Key | Description |
|-----|-------------|
| `\ Enter` | Newline (quick) |
| `Ctrl J` | Newline (control seq) |
| `v / V (vim mode)` | Visual / visual-line mode with selection |
| `/ (vim NORMAL)` | Reverse history search (like Ctrl+R) |

### Prefixes

| Key | Description |
|-----|-------------|
| `/` | Slash command |
| `!` | Direct bash; file path autocomplete; Claude responds to output **NEW** |
| `@` | File mention + autocomplete |

### Session Picker

| Key | Description |
|-----|-------------|
| `↑↓` | Navigate |
| `←→` | Expand/collapse |
| `R` | Rename |
| `/` | Search |
| `Ctrl+A` | Show all projects (in /resume) |

## 🔌 MCP Servers

### Add Servers

| Key | Description |
|-----|-------------|
| `--transport http` | Remote HTTP (recommended) |
| `--transport stdio` | Local process |
| `--transport sse` | Remote SSE |

### Scopes

| Key | Description |
|-----|-------------|
| `Local` | settings.local.json (you only) |
| `Project` | .mcp.json (shared/VCS) |
| `User` | ~/.claude.json (global) |

### Manage

| Key | Description |
|-----|-------------|
| `/mcp` | Interactive UI |
| `claude mcp list` | List all servers (⏸ = pending approval) |
| `claude mcp serve` | CC as MCP server |
| `claude mcp login <name>` | Authenticate MCP server from CLI; --no-browser for SSH |
| `claude mcp logout <name>` | Revoke MCP server authentication from CLI |
| `Elicitation` | Servers request input mid-task |
| `_meta maxResultSizeChars` | Override result size up to 500K |
| `alwaysLoad` | Skip tool-search deferral for server tools |
| `workspace` | Reserved server name — skipped with warning |
| `${CLAUDE_PROJECT_DIR}` | Reference project dir in MCP server commands |

## ⚡ Slash Commands

### Session

| Key | Description |
|-----|-------------|
| `/clear` | Clear conversation |
| `/compact [focus]` | Compact context |
| `/resume` | Resume/switch session (includes bg sessions) |
| `/rename [name]` | Name current session |
| `/branch [name]` | Branch conversation (/fork alias) |
| `/context` | Visualize context (grid) |
| `/diff` | Interactive diff viewer (keyboard-scrollable detail) |
| `/rewind` | Rewind conv / code checkpoint; resume from before /clear (/undo alias) |
| `/recap` | Context summary when returning to session |
| `/focus` | Toggle focus view |
| `/export` | Export conversation |
| `/goal [condition]` | Set completion condition; Claude works across turns until met |
| `/cd [path]` | Move session to new working directory without breaking prompt cache |

### Config

| Key | Description |
|-----|-------------|
| `/config` | Open settings; key=value sets any setting; --help lists shorthand keys |
| `/model [model]` | Switch model; Org/Role default when admin sets one (←→ effort, s = session only) **NEW** |
| `/fast [on|off]` | Toggle fast mode |
| `/theme` | Change color theme; Auto matches terminal |
| `/permissions` | View/update permissions |
| `/effort [level]` | Set effort; interactive slider (low–max; Faster/Smarter labels) |
| `/keybindings` | Customize keyboard shortcuts |
| `/terminal-setup` | Configure terminal keybindings |

### Tools

| Key | Description |
|-----|-------------|
| `/init` | Create CLAUDE.md |
| `/memory` | Edit CLAUDE.md files |
| `/mcp` | Manage MCP servers |
| `/hooks` | Manage hooks |
| `/skills` | List available skills |
| `/agents` | Manage agents |
| `/reload-plugins` | Hot-reload plugins |
| `/reload-skills` | Re-scan skill directories without restarting |
| `/add-dir <path>` | Add working directory |
| `/chrome` | Select connected browser for Chrome integration |
| `/plugin [name]` | Browse, install, enable/disable plugins and marketplaces |
| `/plugin list [--enabled|--disabled]` | List installed plugins with status filters |
| `/ide` | Connect to IDE for diagnostics and editor integration |

### Special

| Key | Description |
|-----|-------------|
| `/btw <question>` | Side question (no context); ←/→ step through earlier answers |
| `/plan [desc]` | Plan mode (+ auto-start) |
| `/loop [interval]` | Recurring task (/proactive alias) |
| `/bg [prompt]` | Fork current turn into an attachable background session |
| `/voice` | Push-to-talk voice (20 langs) |
| `/doctor` | Diagnose installation |
| `/pr-comments [PR]` | Fetch GitHub PR comments |
| `/remote-control` | Bridge to claude.ai/code (/rc) |
| `/usage` | Usage stats with per-category breakdown, cost, and rate status |
| `/schedule` | Cloud scheduled tasks |
| `/security-review` | Security analysis of changes |
| `/usage-credits` | View usage credits (renamed from /extra-usage) |
| `/feedback` | Submit feedback; include recent sessions (alias: /bug) |
| `/powerup` | Interactive lessons + animated demos |
| `/workflows` | View dynamic workflow runs; press f to filter status |
| `/logout` | Sign out (in agents view) |

## 📁 Memory & Files

### CLAUDE.md Locations

| Key | Description |
|-----|-------------|
| `./CLAUDE.md` | Project (team-shared) |
| `~/.claude/CLAUDE.md` | Personal (all projects) |
| `/etc/claude-code/` | Managed (org-wide) |

### Rules & Import

| Key | Description |
|-----|-------------|
| `.claude/rules/*.md` | Project rules |
| `~/.claude/rules/*.md` | User rules |
| `paths: frontmatter` | Path-specific rules |
| `@path/to/file` | Import in CLAUDE.md |

### Auto Memory

| Key | Description |
|-----|-------------|
| `~/.claude/projects/<proj>/memory/` | Auto-loaded per project |
| `MEMORY.md` | Memory index + topic files |

## 💡 Workflows & Tips

### Plan Mode

| Key | Description |
|-----|-------------|
| `Shift Tab` | Normal → Auto-Accept → Plan |
| `--permission-mode plan` | Start in plan mode |
| `Auto mode` | Built-in for Max; Bedrock/Vertex/Foundry via CLAUDE_CODE_ENABLE_AUTO_MODE |

### Thinking & Effort

| Key | Description |
|-----|-------------|
| `Alt T` | Toggle thinking on/off |
| `"ultrathink"` | Max effort for turn |
| `Ctrl O` | Toggle verbose transcript |
| `/effort` | ○ low · ◐ med · ◑ xhigh · ● high/max (Faster↔Smarter) |

### Git Worktrees

| Key | Description |
|-----|-------------|
| `--worktree name` | Isolated branch per feature |
| `isolation: worktree` | Agent in own worktree |
| `sparsePaths` | Checkout only needed dirs |
| `/batch` | Auto-creates worktrees |
| `EnterWorktree (switch)` | Switch between Claude-managed worktrees mid-session |

### Voice Mode

| Key | Description |
|-----|-------------|
| `/voice` | Enable push-to-talk |
| `Space (hold)` | Record, release to send |
| `20 languages` | EN, ES, FR, DE, CZ, PL… |

### Context Management

| Key | Description |
|-----|-------------|
| `/context` | Usage + optimization tips |
| `/compact [focus]` | Compress with focus |
| `Auto-compact` | ~95% capacity |
| `Summarize up to here` | Rewind menu option — compress earlier context, keep recent turns |
| `1M context` | Opus 4.8 (Max/Team/Ent) |
| `CLAUDE.md` | Survives compaction! |

### Session Power Moves

| Key | Description |
|-----|-------------|
| `claude -c` | Continue last conv |
| `claude -r "name"` | Resume by name |
| `/btw question` | Side Q, no context cost |

### SDK / Headless

| Key | Description |
|-----|-------------|
| `claude -p "query"` | Non-interactive |
| `--output-format json` | Structured output |
| `--max-budget-usd 5` | Cost cap |
| `cat file | claude -p` | Pipe input |

### Scheduling & Remote

| Key | Description |
|-----|-------------|
| `/loop 5m msg` | Recurring task (/proactive) |
| `/rc` | Remote Control |
| `--remote` | Web session |
| `Push notifications` | Mobile push via Remote Control |
| `API key → no cloud` | API key / non-Anthropic ANTHROPIC_BASE_URL disables RC, /schedule, MCP, notifications **NEW** |
| `Dynamic workflows` | Orchestrates tens–hundreds of agents; triggers on 'run a workflow', 'workflow:' |

## 🖥️ CLI & Flags

### Core Commands

| Key | Description |
|-----|-------------|
| `claude` | Interactive |
| `claude "q"` | With prompt |
| `claude -p "q"` | Headless |
| `claude -c` | Continue last |
| `claude -r "n"` | Resume |
| `claude update` | Update |
| `claude plugin tag` | Create release git tag for plugin |
| `claude plugin prune` | Remove orphaned auto-installed plugins |
| `claude ultrareview [target]` | Run /ultrareview non-interactively; --json for raw |
| `claude plugin init <name>` | Scaffold a new plugin in .claude/skills |
| `claude agents` | Agent dashboard; --cwd, --add-dir, --settings, --mcp-config, --model, --effort, --json |
| `claude agents --json` | List live sessions as JSON; --all includes completed; id/state fields |
| `claude plugin details <name>` | Show plugin components, LSP servers, and projected token cost |
| `claude --bg --exec '<cmd>'` | Run shell command as attachable background session |
| `claude plugin enable <name>` | Enable a plugin; force-enables its dependencies |
| `claude plugin disable <name>` | Disable a plugin; refuses if a dependent is enabled |

### Key Flags

| Key | Description |
|-----|-------------|
| `--model` | Set model |
| `-w` | Git worktree |
| `-n / --name` | Session name |
| `--add-dir` | Add dir |
| `--agent` | Use agent |
| `--allowedTools` | Pre-approve |
| `--output-format` | json/stream |
| `--json-schema` | Structured |
| `--max-turns` | Limit turns |
| `--max-budget-usd` | Cost cap |
| `--verbose` | Verbose |
| `--bare` | Minimal headless (no hooks/LSP) |
| `--remote` | Web session |
| `--from-pr` | Load PR/MR from GitHub/GitLab/Bitbucket/GHE |
| `--effort` | low/med/xhigh/high/max |
| `--permission-mode` | plan/default/… |
| `--dangerously-skip-permissions` | Skip all prompts; catastrophic rm still prompts ⚠️ |
| `--chrome` | Chrome |
| `--fallback-model` | Fallback when primary unavailable (interactive + headless) |
| `--thinking` | disabled turns off thinking on default-thinking models |
| `--plugin-dir` | Load plugin from directory or .zip archive |
| `--plugin-url` | Fetch plugin .zip archive from URL for session |
| `--console` | Auth via Anthropic Console |
| `--safe-mode` | Start with all customizations disabled for troubleshooting |

## 🤖 Skills & Agents

### Built-in Skills

| Key | Description |
|-----|-------------|
| `/code-review [effort]` | Code review with effort; --comment for inline PR comments, --fix to apply findings |
| `/batch` | Large parallel changes (5-30 worktrees) |
| `/debug [desc]` | Troubleshoot from debug log |
| `/loop [interval]` | Recurring task (/proactive alias) |
| `/claude-api` | Load API + SDK reference |
| `/ultrareview [PR#]` | Cloud code review (parallel multi-agent) |
| `/less-permission-prompts` | Scan transcripts for allowlist proposals |
| `/simplify` | Cleanup-only review (reuse, simplify, efficiency, altitude) and apply fixes |

### Custom Skill Locations

| Key | Description |
|-----|-------------|
| `.claude/skills/<name>/` | Project skills (auto-loaded as plugins) |
| `~/.claude/skills/<name>/` | Personal skills |
| `Nested .claude/skills` | Nested skill dirs load; clashes show as <dir>:<name> |
| `Nested .claude/ priority` | Agent/workflow/output-style closest to cwd wins on collision |

### Skill Frontmatter

| Key | Description |
|-----|-------------|
| `description` | Auto-invocation trigger |
| `allowed-tools` | Skip permission prompts |
| `disallowed-tools` | Remove tools from model while skill is active |
| `model` | Override model for skill |
| `effort` | Override effort level |
| `context: fork` | Run in subagent |
| `$ARGUMENTS` | User input placeholder |
| `${CLAUDE_SKILL_DIR}` | Skill's own directory |
| `!`cmd`` | Dynamic context injection |
| `\$` | Escape literal $ before digit in command bodies |
| `bin/` | Plugin ships executables |
| `keep-coding-instructions` | Frontmatter for plugin output styles |
| `monitors` | Plugin background monitors (auto-arm on session/skill) |
| `slash commands (Skill)` | Model discovers/invokes built-in commands |
| `${CLAUDE_EFFORT}` | Current effort level (skills, hooks, Bash tool) |
| `root SKILL.md` | Plugin skill without skills/ subdirectory |

### Built-in Agents

| Key | Description |
|-----|-------------|
| `Explore` | Fast read-only (Haiku) |
| `Plan` | Research for plan mode |
| `General` | Full tools, complex tasks |
| `Bash` | Terminal separate context |
| `Workflow` | Dynamic multi-agent orchestration (opt-in); /workflows to view runs |
| `Nesting depth` | Sub-agents can spawn their own sub-agents up to 5 levels deep |

### Agent Frontmatter

| Key | Description |
|-----|-------------|
| `permissionMode` | default/acceptEdits/plan/dontAsk/bypass |
| `isolation: worktree` | Run in git worktree |
| `memory: user|project` | Persistent memory |
| `background: true` | Background task |
| `maxTurns` | Limit agentic turns |
| `SendMessage` | Resume agents (replaces resume) |
| `initialPrompt` | Auto-submit first turn |
| `mcpServers` | Load MCP servers for agent session |

## ⚙️ Config & Env

### Config Files

| Key | Description |
|-----|-------------|
| `~/.claude/settings.json` | User settings |
| `.claude/settings.json` | Project (shared) |
| `.claude/settings.local.json` | Local only |
| `~/.claude.json` | OAuth, MCP, state |
| `.mcp.json` | Project MCP servers |

### Key Settings

| Key | Description |
|-----|-------------|
| `modelOverrides` | Map model picker → custom IDs |
| `worktree.sparsePaths` | Sparse checkout dirs |
| `autoMode.$defaults` | Extend built-in auto mode rules instead of replacing |
| `skillOverrides` | Control skill visibility: off/user-invocable-only/name-only |
| `autoMode.hard_deny` | Block unconditionally regardless of user intent or allow exceptions |
| `autoMode.classifyAllShell` | Route all Bash/PowerShell commands through auto-mode classifier **NEW** |
| `workflowKeywordTrigger` | Explicit phrases only ('run a workflow', 'workflow:'); purple shimmer |
| `disableAllHooks` | Disable all hooks via settings.json / managed settings |
| `requiredMinimumVersion / requiredMaximumVersion` | Managed settings; refuses start if version outside allowed range |
| `fallbackModel` | Up to 3 fallback models tried in order when primary is overloaded |
| `deny: tool-name glob` | * denies all; Tool(param:value) matches input params; allow rejects non-MCP |
| `disableBundledSkills` | Hide bundled skills, workflows, and built-in slash commands from model |
| `sandbox.allowAppleEvents` | Opt-in: let sandboxed commands send Apple Events on macOS |
| `respondToBashCommands` | false keeps ! bash output as context only (default: Claude responds) |
| `sandbox.credentials` | Block sandboxed commands from reading credential files and secret env vars |

### Key Env Vars

| Key | Description |
|-----|-------------|
| `ANTHROPIC_API_KEY` | API key |
| `ANTHROPIC_MODEL` | Default model; org restrictions can override |
| `CLAUDE_CODE_EFFORT_LEVEL` | low/med/high |
| `MAX_THINKING_TOKENS` | 0=off; disables thinking on models that think by default |
| `CLAUDE_EFFORT` | Current effort level in hooks and Bash tool |
| `CLAUDE_PROJECT_DIR` | Project dir passed to MCP stdio servers and hooks env |
| `CLAUDE_CODE_WORKFLOWS` | Enable Workflow tool for multi-agent orchestration |
| `CLAUDE_CODE_SESSION_ID` | Session ID passed to stdio MCP server subprocesses (also on --resume) |
| `CLAUDE_CODE_ENABLE_AUTO_MODE` | Enable auto mode on Bedrock/Vertex/Foundry for Opus 4.7/4.8 |
| `CLAUDE_CODE_SUBAGENT_MODEL` | Set model for subagents and agent-team teammates |
| `MCP_TOOL_TIMEOUT` | Raise per-request MCP tool timeout above 60s default |
| `CLAUDE_CODE_SAFE_MODE` | Env var equivalent of --safe-mode flag |
| `CLAUDE_ENABLE_STREAM_WATCHDOG` | Set 0 to disable; 5-min idle abort+retry on by default for all providers **NEW** |
| `OTEL_LOG_ASSISTANT_RESPONSES` | 1=log assistant responses in OTEL; 0=keep prompts-only; unset follows OTEL_LOG_USER_PROMPTS **NEW** |
| `CLAUDE_CODE_DISABLE_MOUSE_CLICKS` | Disable mouse click/drag/hover in fullscreen mode; wheel scroll still works **NEW** |

### Hooks

| Key | Description |
|-----|-------------|
| `PreToolUse` | Before tool executes |
| `PostToolUse` | After tool executes (duration_ms; can replace output) |
| `Notification` | When Claude sends notification |
| `Stop` | When Claude finishes response (background_tasks, session_crons) |
| `SubagentStop` | When subagent finishes (background_tasks, session_crons) |
| `mcp_tool type` | Invoke MCP tool directly from hook |
| `args: string[]` | Hook exec form — spawn directly without shell |
| `continueOnBlock` | PostToolUse: feed rejection reason back, continue turn |
| `hookSpecificOutput.additionalContext` | Stop/SubagentStop: give Claude feedback, continue turn |
| `SessionStart` | Run on session start/resume; set title, reload skills |
| `ConfigChange` | Fire when settings files change (hot-reload) |

---

*Auto-updated every 6h from [CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md) via GitHub Actions + Claude AI*