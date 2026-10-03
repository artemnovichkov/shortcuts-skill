# macOS Shortcuts Skill

An [Agent Skill](https://agentskills.io) for listing, viewing, and running macOS Shortcuts from Claude Code and other coding agents.

## Features

- **List** all shortcuts on your Mac
- **View** a shortcut in the Shortcuts app
- **Run** a shortcut, with or without input (text or file)

## Requirements

- macOS 12 (Monterey) or later
- [Claude Code](https://code.claude.com) or another agent that supports skills

## Installation

### Claude Code plugin (recommended)

```
/plugin marketplace add artemnovichkov/shortcuts-skill
/plugin install shortcuts@shortcuts-skill
```

Update later with `/plugin marketplace update shortcuts-skill`.

### Skills CLI (any agent)

Works with Claude Code, Codex, Cursor, and [other agents](https://skills.sh):

```bash
# Current project
npx skills add artemnovichkov/shortcuts-skill

# All projects
npx skills add artemnovichkov/shortcuts-skill -g
```

### Manual

Copy `skills/shortcuts` into `~/.claude/skills/` (all projects) or `.claude/skills/` (single project):

```bash
git clone https://github.com/artemnovichkov/shortcuts-skill
cp -r shortcuts-skill/skills/shortcuts ~/.claude/skills/
```

## Usage

Claude picks up the skill automatically when you mention shortcuts:

```
What shortcuts do I have?
Open the "Morning Routine" shortcut
Run "Convert to PDF"
Run "Translate Text" with input "Hello World"
Resize photo.jpg using the "Resize Image" shortcut
```

Or invoke it directly:

```
/shortcuts run "Morning Routine"
```

When installed as a plugin, the command is namespaced: `/shortcuts:shortcuts`.

## How it works

The skill teaches the agent to use the built-in `shortcuts` CLI:

| Command | Description |
| --- | --- |
| `shortcuts list` | List all shortcuts |
| `shortcuts view "<name>"` | Open a shortcut in the Shortcuts app |
| `shortcuts run "<name>"` | Run a shortcut |
| `shortcuts run "<name>" --input-path <file>` | Run with file input |
| `echo "text" \| shortcuts run "<name>"` | Run with text input |

See [`examples.md`](skills/shortcuts/examples.md) for more scenarios.

## Troubleshooting

- **Shortcut not found** — names are case-sensitive; ask Claude to list shortcuts first.
- **Permission prompts** — some shortcuts need access to files, contacts, etc. Grant it when macOS asks.
- **Skill not triggering** — run `/skills` to check it's loaded, or invoke it with `/shortcuts`.

## License

[MIT](LICENSE)

## Resources

- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [Claude Code plugins](https://code.claude.com/docs/en/plugins)
- [Shortcuts User Guide for Mac](https://support.apple.com/guide/shortcuts-mac)
