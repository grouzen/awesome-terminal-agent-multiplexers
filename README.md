# Awesome Terminal Agent Multiplexers

An opinionated guide to terminal-centric tools for running, organizing, and monitoring multiple AI coding agents.

Related search terms: `AI agent session manager`, `parallel coding agents`, `agentic terminal workspace`, `tmux/worktree agent manager`.

## What Is a Terminal Agent Multiplexer?

A terminal agent multiplexer is software that helps you:

- launch multiple CLI agents in parallel
- keep them isolated with separate terminals, sessions, branches, or worktrees
- see which agents are running, waiting, blocked, or done
- jump between them quickly
- resume or recover sessions after disconnects or restarts

The category sits between raw terminal multiplexers like `tmux`/`zellij` and heavier browser/IDE-style agent workspaces.

## Why These Tools Exist

`tmux`, `zellij`, `WezTerm`, and `kitty` already solve persistence, panes, tabs, and layout. What they do not solve on their own is agent orchestration.

Once you go from one agent to five, the hard parts become:

- tracking which agent owns which branch or worktree
- knowing which agent is waiting for input
- recovering context after terminal crashes or machine restarts
- reviewing diffs and merging results without manual cleanup
- wiring notifications, hooks, approvals, or mobile access into the workflow

That is the gap terminal agent multiplexers try to close.

## `tmux` / `zellij` vs Terminal Agent Multiplexers

| Capability | `tmux` / `zellij` | Terminal agent multiplexers |
| --- | --- | --- |
| Session persistence | Yes | Yes |
| Panes, tabs, layouts | Yes | Yes |
| Agent status awareness | No | Usually yes |
| Worktree lifecycle | Manual | Often built in |
| Diff / review workflow | Manual | Often built in |
| Notifications when an agent needs attention | Manual | Often built in |
| Remote or mobile control | Manual | Sometimes built in |
| Hooks / APIs / orchestration | Minimal | Often opinionated |
| Multi-agent UX | Generic terminal UX | Agent-first UX |

## Main Comparison

Direct peers belong here. Adjacent tmux/worktree tools and broader terminal platforms are listed later.

| Project | Product shape | Runtime model | Worktree support | Agent scope | Remote / web | Automation / API | Best fit |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [flowmux](https://github.com/grouzen/flowmux) | Terminal-native agent multiplexer | `tmux`-based terminal multiplexer architecture | Built in | Claude Code, Codex, OpenCode | No | No public API | Keyboard-first agent-aware terminal multiplexer with grid-based terminal workflow |
| [herdr](https://github.com/ogulcancelik/herdr) | Terminal-native agent multiplexer | Standalone Rust multiplexer built on raw PTY control | Built in | Broad detection plus official integrations | SSH / remote attach | Socket API | Real terminal panes, workspaces, and agent awareness in a self-contained multiplexer |
| [Agent of Empires](https://github.com/agent-of-empires/agent-of-empires) | Agent control plane | `tmux`-backed TUI plus web dashboard | Built in | Broad multi-agent support | Browser, PWA, phone access | CLI and HTTP API | Remote monitoring, structured views, and optional sandboxing |
| [Agent Deck](https://github.com/asheshgoplani/agent-deck) | Agent command center | `tmux`-backed TUI | Built in | Claude, Codex, OpenCode, Pi and others | No web UI | Conductor workflow, MCP and skills management | Session fleet management and notification-heavy orchestration |
| [amux](https://github.com/andyrewlee/amux) | Terminal UI for parallel agents | `tmux`-backed TUI | Built in and importable | Claude Code, Codex, Gemini, Amp, OpenCode, Droid | No | Workspace setup hooks | Workspace-first parallel coding in a simple TUI |
| [chloe](https://github.com/KevinEdry/chloe) | Terminal-native orchestrator | Standalone Rust TUI | Git worktrees and Jujutsu workspaces | Claude Code, Gemini CLI, Amp, OpenCode | No | No public API | Lightweight terminal-native orchestration with Kanban-like task tracking |
| [dmux](https://github.com/formkit/dmux) | Worktree-first agent runner | `tmux`-backed TUI | Built in | Broad CLI-agent support | No | Lifecycle hooks | Fast pane-per-task workflows with worktree isolation and merge helpers |
| [ntm](https://github.com/Dicklesworthstone/ntm) | Orchestration layer | `tmux`-backed control plane | Session-oriented, worktree use is optional | Multi-agent orchestration | No browser-first UI | REST, SSE, WebSocket, OpenAPI | Policy-driven multi-agent automation and approvals |

## Recommended Starting Points

- [flowmux](https://github.com/grouzen/flowmux) if you want a fully terminal-native AI agent multiplexer with a keyboard-first grid dashboard, per-project grouping, and `tmux`-based persistence.
- [herdr](https://github.com/ogulcancelik/herdr) if you want a fully terminal-native AI agent multiplexer with native workspaces, tabs, panes, remote attach, and a standalone PTY-driven architecture.
- [Agent of Empires](https://github.com/agent-of-empires/agent-of-empires) if remote access, mobile monitoring, structured web views, or container sandboxing matter more than staying purely terminal-native.
- [workmux](https://github.com/raine/workmux) if your mental model is still “git worktrees plus my existing terminal stack,” and you want orchestration glue more than a dedicated agent dashboard.

## Core Terminal Agent Multiplexers

- [Agent Deck](https://github.com/asheshgoplani/agent-deck) - An AI agent command center built around `tmux` sessions, status tracking, worktrees, MCP management, and a conductor pattern for supervising fleets of sessions.
- [Agent of Empires](https://github.com/agent-of-empires/agent-of-empires) - A session manager for AI coding agents with a TUI, a web dashboard, worktrees, optional Docker sandboxing, and remote phone-friendly access.
- [amux](https://github.com/andyrewlee/amux) - A `tmux`-backed TUI for parallel coding agents with a workspace-first model, diff access, and minimal wrapper behavior.
- [chloe](https://github.com/KevinEdry/chloe) - A terminal-native Rust orchestrator that mixes PTY panes with task tracking, Kanban views, and both Git worktrees and Jujutsu workspaces.
- [dmux](https://github.com/formkit/dmux) - A pane-per-task workflow tool that creates isolated worktrees and branches automatically, then helps merge or open PRs when tasks finish.
- [flowmux](https://github.com/grouzen/flowmux) - A fully capable terminal-native AI agent multiplexer built on top of `tmux`, with a grid dashboard, per-project grouping, agent status tracking, worktree creation, and persistent per-agent terminals.
- [herdr](https://github.com/ogulcancelik/herdr) - A fully capable terminal-native AI agent multiplexer implemented as its own Rust terminal multiplexer, with panes, tabs, workspaces, remote attach, and a socket API built around raw PTY control.
- [ntm](https://github.com/Dicklesworthstone/ntm) - A structured multi-agent orchestration system on top of `tmux` with policies, approvals, durable state, and machine-consumable APIs.

## Adjacent tmux / Worktree Orchestration Tools

These are relevant and useful, but they are not the same product shape as the main comparison set.

- [ittybitty](https://github.com/adamwulf/ittybitty) - A single Bash script for spawning and supervising multiple Claude Code agents, each in its own `tmux` session and git worktree. Great if you want minimal dependencies and a Claude-specific workflow instead of a general multiplexer product.
- [tws](https://github.com/ytaskiran/tws) - A `tmux` workspace manager that adds persistent threads, notes, fuzzy search, recent-session jumping, and an agents view across existing sessions.
- [workmux](https://github.com/raine/workmux) - An opinionated workflow layer for git worktrees plus `tmux` windows, with dashboards, sidebars, hooks, sandboxing options, and alternative backends including `kitty`, `WezTerm`, and `zellij`.

## Broader Terminal Platforms For Agent Workflows

These are worth mentioning because they compete for the same mindshare, but they are broader terminal platforms rather than direct terminal agent multiplexer peers.

### Open Source or Source-Available

- [cmux](https://cmux.com) - A native macOS terminal for coding agents built on `libghostty`, with vertical tabs, notification rings, split panes, an in-app browser, and a CLI/socket automation story.
- [Ghostty](https://github.com/ghostty-org/ghostty) - A fast native terminal emulator and embeddable library (`libghostty`) that matters here both as a modern terminal in its own right and as a substrate for tools like `cmux`.
- [kitty](https://github.com/kovidgoyal/kitty) - A fast, GPU-based, feature-rich terminal that remains a strong baseline for power users who want a great terminal substrate and do not need agent-aware orchestration built in.
- [Tabby](https://github.com/Eugeny/tabby) - A highly configurable terminal and SSH client with split panes, persistent tabs, connection management, completion notifications, and a plugin model.
- [Wave Terminal](https://github.com/wavetermdev/waveterm) - An open-source, AI-integrated terminal with durable SSH sessions, block/workspace UI, built-in editor and previews, and multi-provider AI support. Broader than a multiplexer, but increasingly relevant.
- [Warp](https://github.com/warpdotdev/Warp) - An open-source agentic development environment and terminal platform with its own coding agent plus support for CLI agents like Claude Code, Codex, and Gemini CLI. Broader than a terminal multiplexer, but relevant to the same workflows.
- [WezTerm](https://github.com/wez/wezterm) - A cross-platform terminal emulator and multiplexer written in Rust. It is one of the strongest foundations for custom agent workflows, but it is not agent-aware by default.

## Terminology Note

This category is still emerging. Some tools are:

- true terminal-native AI agent multiplexers
- tmux with plugins to get closer to agent-aware control planes
- broader agentic terminals or browser/desktop workspaces

That is why this README separates direct multiplexer peers from adjacent orchestration tools and broader terminal platforms.
