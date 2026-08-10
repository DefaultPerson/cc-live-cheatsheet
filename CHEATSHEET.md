# Claude Code Cheatsheet v2.1.227

> Auto-generated from [cheatsheet.json](cheatsheet.json) | [Visual version](cheatsheet.png) | [Interactive](https://defaultperson.github.io/cc-live-cheatsheet/)

## Recent Changes

- SendMessage initiates with Remote Control sessions by name via ListAgents *(v2.1.225)*
- Gateway spend-limit support: usage warning names cap, reset time, operator message *(v2.1.225)*
- Workspace trust prompt for claude agents in untrusted directories *(v2.1.225)*
- Cross-session messages now expire/notify in headless sessions and startup *(v2.1.225)*
- RC photos from Claude app shown directly to Claude instead of disk read *(v2.1.225)*

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
| `Ctrl+X Ctrl+K` | Kill bg agents; agents view: remove session + worktree, preserve unpushed commits |
| `Ctrl+Alt+F` | Toggle Focus view (VSCode: hide tool activity behind expandable summary) |
| `Esc Esc` | Rewind / undo |
| `←` | Open agents view |
| `{ / }` | Jump between user prompts (transcript view) |
| `?` | Show keyboard shortcuts (transcript view) |

### Mode Switching

| Key | Description |
|-----|-------------|
| `Shift Tab` | Cycle permission modes |
| `Alt P` | Switch model |
| `Alt T` | Toggle thinking on/off |

### Input

| Key | Description |
|-----|-------------|
| `\ Enter` | Newline (quick) |
| `Ctrl J` | Newline (control seq) |
| `v / V (vim mode)` | Visual / visual-line mode with selection |
| `/ (vim NORMAL)` | Reverse history search (like Ctrl+R) |
| `:shortcode:` | Emoji autocomplete in prompt; accepts alternate shortcodes (:thumbsup:, :love:) |

### Prefixes

| Key | Description |
|-----|-------------|
| `/` | Slash command |
| `!` | Direct bash; file path autocomplete; Claude responds to output |
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
| `workspace` | Reserved names — skipped: workspace, Claude Browser, Claude Preview |
| `${CLAUDE_PROJECT_DIR}` | Reference project dir in MCP server commands |
| `roots/list` | Additional working dirs advertised; notifications/roots/list_changed on changes |

## ⚡ Slash Commands

### Session

| Key | Description |
|-----|-------------|
| `/clear` | Clear conversation |
| `/compact [focus]` | Compact context |
| `/resume` | Resume/switch session; agent view: picker of past sessions incl. deleted |
| `/rename [name]` | Name current session |
| `/branch [name]` | Branch conversation |
| `/context` | Visualize context (grid) |
| `/diff` | Interactive diff viewer (keyboard-scrollable detail) |
| `/rewind` | Rewind conv / code checkpoint; resume from before /clear (/undo alias) |
| `/recap` | Context summary when returning to session |
| `/focus` | Toggle focus view |
| `/goal [condition]` | Set completion condition; Claude works across turns until met |
| `/cd [path]` | Move session to new working directory with path suggestions; no prompt cache break |
| `/fork` | Copy conversation into new background session with its own worktree |
| `/subtask` | Launch in-session subagent (former /fork behavior) |

### Config

| Key | Description |
|-----|-------------|
| `/config` | Open settings; key=value sets any setting; --help lists shorthand keys |
| `/model [model]` | Switch model; Org/Role default when admin sets one (←→ effort, s = session only) |
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
| `/reload-plugins` | Hot-reload plugins |
| `/reload-skills` | Re-scan skill directories without restarting |
| `/add-dir <path>` | Add working directory |
| `/chrome` | Select connected browser for Chrome integration |
| `/plugin [name]` | Browse, install, enable/disable plugins and marketplaces |
| `/plugin list [--enabled|--disabled]` | List installed plugins with status filters |
| `/ide` | Connect to IDE for diagnostics and editor integration |
| `/review` | Alias for /code-review |

### Special

| Key | Description |
|-----|-------------|
| `/btw <question>` | Side question (no context); bare reopens panel; ←/→ browse answers |
| `/plan [desc]` | Plan mode (+ auto-start) |
| `/loop [interval]` | Recurring task (/proactive alias) |
| `/bg [prompt]` | Fork current turn into an attachable background session |
| `/voice` | Push-to-talk voice (20 langs) |
| `/doctor` | Setup checkup: diagnose/fix issues; suggest CLAUDE.md trim (/checkup alias) |
| `/pr-comments [PR]` | Fetch GitHub PR comments |
| `/remote-control` | Bridge to claude.ai/code (/rc); auto-start only via user-scope settings |
| `/usage` | Usage stats with per-category breakdown, cost, and rate status |
| `/schedule` | Cloud scheduled tasks |
| `/security-review` | Security analysis of changes |
| `/usage-credits` | View usage credits (renamed from /extra-usage) |
| `/feedback` | Submit feedback; include recent sessions (alias: /bug) |
| `/workflows` | View dynamic workflow runs; press f to filter status |
| `/status` | Show session status, warnings, session kind (interactive/attached/unattended) |

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
| `MEMORY.md` | Memory index + topic files; errors over read limit (loaded content only) |
| `modified (frontmatter)` | ISO timestamp in memory file frontmatter |

## 💡 Workflows & Tips

### Plan Mode

| Key | Description |
|-----|-------------|
| `Shift Tab` | Manual → Auto-Accept → Plan |
| `⏸ footer badge` | Shows active manual permission mode |
| `--permission-mode plan` | Start in plan mode |
| `Auto mode` | Max & Bedrock/Vertex/Foundry; disableAutoMode; classifier adjudicates edge cases |

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
| `isolation: worktree` | Agent in own worktree; auto-commits, pushes, opens draft PR |
| `sparsePaths` | Checkout only needed dirs |
| `/batch` | Auto-creates worktrees |
| `EnterWorktree (switch)` | Switch between Claude-managed worktrees; confirms if outside project dir |

### Voice Mode

| Key | Description |
|-----|-------------|
| `/voice` | Enable push-to-talk |
| `Space (hold)` | Record, release to send |
| `20 languages` | EN, ES, FR, DE, CZ, PL… |

### Context Management

| Key | Description |
|-----|-------------|
| `/context` | Usage + optimization tips; warns if exceeding context window |
| `/compact [focus]` | Compress with focus |
| `Auto-compact` | ~95% capacity |
| `Summarize up to here` | Rewind menu option — compress earlier context, keep recent turns |
| `1M context` | Sonnet 5 (default) + Opus 5 + Opus 4.8 (Max/Team/Ent) |
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
| `--max-budget-usd 5` | Cost cap; also stops background subagents when reached |
| `cat file | claude -p` | Pipe input |

### Scheduling & Remote

| Key | Description |
|-----|-------------|
| `/loop 5m msg` | Recurring task (/proactive) |
| `/rc` | Remote Control |
| `--remote` | Web session |
| `Push notifications` | Mobile push via Remote Control |
| `API key → no cloud` | API key / non-Anthropic ANTHROPIC_BASE_URL disables RC, /schedule, MCP, notifications |
| `Dynamic workflows` | Orchestrates agents; default medium (<15); triggers on 'run a workflow', 'workflow:' |
| `Self-hosted runner` | Own machines/containers as CC session hosts; claude self-hosted-runner (Team/Ent) **NEW** |

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
| `claude plugin prune` | Remove orphaned auto-installed plugins |
| `claude plugin init <name>` | Scaffold a new plugin in .claude/skills |
| `claude agents` | Agent dashboard; --cwd, --add-dir, --settings, --mcp-config, --model, --effort, --json |
| `claude agents --json` | List live sessions as JSON; --all includes completed; id/state fields |
| `claude --bg --exec '<cmd>'` | Run shell command as attachable background session |
| `claude plugin enable <name>` | Enable a plugin; force-enables its dependencies |
| `claude plugin disable <name>` | Disable a plugin; refuses if a dependent is enabled |
| `claude auto-mode reset` | Restore default auto-mode config; --yes skips confirmation |
| `claude self-hosted-runner` | Turn your machines/containers into CC session hosts (Team/Ent) **NEW** |
| `archive (plugin source)` | Install plugins from zip over HTTPS; SHA-256 pinning **NEW** |

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
| `--max-budget-usd` | Cost cap; also stops background subagents when reached |
| `--verbose` | Verbose |
| `--remote` | Web session |
| `--from-pr` | Load PR/MR from GitHub/GitLab/Bitbucket/GHE |
| `--effort` | low/med/xhigh/high/max |
| `--permission-mode` | plan/manual/… |
| `--dangerously-skip-permissions` | Skip all prompts; catastrophic rm (incl. $()/backticks) still prompts ⚠️ |
| `--chrome` | Chrome |
| `--fallback-model` | Fallback when primary unavailable (interactive + headless) |
| `--thinking` | disabled turns off thinking on default-thinking models |
| `--plugin-dir` | Load plugin from directory or .zip archive |
| `--plugin-url` | Fetch plugin .zip archive from URL for session |
| `--safe-mode` | Start with all customizations disabled for troubleshooting |
| `--ax-screen-reader` | Opt-in plain-text rendering for screen reader users |
| `--teleport <session id>` | Continue a cloud session locally **NEW** |

## 🤖 Skills & Agents

### Built-in Skills

| Key | Description |
|-----|-------------|
| `/verify` | Verification; no longer auto-invoked by Claude |
| `/code-review [level] [pr#]` | Reviews current diff or PR; remembers last effort; --comment, --fix; ultra for deep cloud |
| `/deep-research [topic]` | Deep research; no longer auto-invoked by Claude |
| `/batch` | Large parallel changes (5-30 worktrees) |
| `/debug [desc]` | Troubleshoot from debug log |
| `/loop [interval]` | Recurring task (/proactive alias) |
| `/claude-api` | Load API + SDK reference |
| `/ultrareview [PR#]` | Cloud code review (parallel multi-agent) |
| `/less-permission-prompts` | Scan transcripts for allowlist proposals |
| `/simplify` | Cleanup-only review (reuse, simplify, efficiency, altitude) and apply fixes |
| `/dataviz` | Chart and dashboard design guidance; runnable color-palette validator |

### Custom Skill Locations

| Key | Description |
|-----|-------------|
| `.claude/skills/<name>/` | Project skills (auto-loaded as plugins) |
| `~/.claude/skills/<name>/` | Personal skills |
| `Nested .claude/skills` | Nested skill dirs load; clashes show as <dir>:<name> |
| `Nested .claude/ priority` | Agent/workflow/output-style closest to cwd wins on collision |
| `Stacked invocation` | Chain up to 5 skills: /skill-a /skill-b do XYZ |

### Skill Frontmatter

| Key | Description |
|-----|-------------|
| `description` | Auto-invocation trigger |
| `allowed-tools` | Skip permission prompts |
| `disallowed-tools` | Remove tools from model while skill is active |
| `model` | Override model for skill |
| `effort` | Override effort level |
| `context: fork` | Run in background subagent by default; background: false to opt out |
| `$ARGUMENTS` | User input placeholder |
| `${CLAUDE_SKILL_DIR}` | Skill's own directory |
| `!`cmd`` | Dynamic context injection |
| `bin/` | Plugin ships executables |
| `keep-coding-instructions` | Frontmatter for plugin output styles |
| `monitors` | Plugin background monitors (auto-arm on session/skill) |

### Built-in Agents

| Key | Description |
|-----|-------------|
| `Explore` | Fast read-only (inherits session model, capped at opus) |
| `Plan` | Research for plan mode |
| `General` | Full tools, complex tasks |
| `Bash` | Terminal separate context |
| `Workflow` | Dynamic multi-agent orchestration (opt-in); /workflows to view runs |
| `Nesting depth` | Sub-agents nest up to depth 3; set CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH=1 to disable |

### Agent Frontmatter

| Key | Description |
|-----|-------------|
| `permissionMode` | default/acceptEdits/plan/dontAsk/bypass |
| `isolation: worktree` | Run in git worktree |
| `memory: user|project` | Persistent memory |
| `background: true` | Background task |
| `maxTurns` | Limit agentic turns |
| `SendMessage` | Resume agents; cross-session ListAgents; start RC sessions by name (macOS/Linux) **NEW** |
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
| `disableAllHooks` | Disable all hooks via settings.json / managed settings |
| `fallbackModel` | Up to 3 fallback models tried in order when primary is overloaded |
| `deny: tool-name glob` | * denies all; Tool(param:value) matches; Write/Glob/NotebookEdit→Edit/Read; dir/** cwd-only in hooks |
| `disableBundledSkills` | Hide bundled skills, workflows, and built-in slash commands from model |
| `sandbox.credentials` | Block credentials; mask, extract, JWT maskClaims, AWS SigV4; needs tlsTerminate **NEW** |
| `sandbox.network.strictAllowlist` | Deny non-allowlisted hosts for sandboxed commands without prompting |
| `disableAutoMode` | Disable auto mode in settings.json |
| `axScreenReader` | Opt-in plain-text rendering; announces permission mode changes |
| `"owner/*" marketplaces` | Wildcard in strictKnownMarketplaces/blockedMarketplaces for all org repos **NEW** |
| `crossSessionInbound` | Hold cross-session messages for approval in bypass-permissions sessions **NEW** |
| `dialogExpiry` | Expiry for cross-session message approval dialogs **NEW** |

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
| `CLAUDE_CODE_SUBAGENT_MODEL` | Set model for subagents and agent-team teammates |
| `CLAUDE_CODE_MAX_CONCURRENT_SUBAGENTS` | Cap on concurrently-running subagents (default 20) |
| `CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH` | Nested subagent spawning; default depth 3; set 1 to disable |
| `CLAUDE_CODE_DISABLE_1M_CONTEXT` | Hold 1M-window models to 200K via auto-compaction **NEW** |
| `CLAUDE_CODE_DISABLE_UNKNOWN_MODEL_WINDOW_ENFORCEMENT` | Restore pre-223 behavior for unknown model IDs **NEW** |
| `ANTHROPIC_BEDROCK_REGION_PREFIX` | Prefer specific Bedrock cross-region inference profile over AWS_REGION **NEW** |

### Hooks

| Key | Description |
|-----|-------------|
| `PreToolUse` | Before tool executes |
| `PostToolUse` | After tool executes (duration_ms; can replace output) |
| `Notification` | When Claude sends notification; agent_needs_input / agent_completed from bg agents |
| `Stop` | When Claude finishes response (background_tasks, session_crons) |
| `SubagentStop` | When subagent finishes (background_tasks, session_crons) |
| `mcp_tool type` | Invoke MCP tool directly from hook |
| `args: string[]` | Hook exec form — spawn directly without shell |
| `continueOnBlock` | PostToolUse: feed rejection reason back, continue turn |
| `hookSpecificOutput.additionalContext` | Stop/SubagentStop: give Claude feedback, continue turn |
| `SessionStart` | Run on session start/resume; source="fork" for forks; set title, reload skills |
| `ConfigChange` | Fire when settings files change (hot-reload) |
| `DirectoryAdded` | Fires after /add-dir or SDK register_repo_root registers new working dir |

---

*Auto-updated every 6h from [CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md) via GitHub Actions + Claude AI*