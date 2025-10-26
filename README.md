# macOS Shortcuts Skill for Claude Code

A Claude Code skill that enables interaction with macOS Shortcuts directly from your terminal through Claude.

## Features

This skill provides three main capabilities:

1. **List Shortcuts** - View all available shortcuts on your Mac
2. **View Shortcuts** - Open a specific shortcut in the Shortcuts app
3. **Run Shortcuts** - Execute shortcuts with optional input parameters

## Installation

### Option 1: Project-Level Installation (Recommended for specific projects)

1. Clone or copy this repository to your project:
   ```bash
   git clone <repository-url> shortcuts-skill
   cd shortcuts-skill
   ```

2. The skill is located in `.claude/skills/shortcuts/` and will be automatically available when you use Claude Code in this directory.

### Option 2: Personal Installation (Available in all projects)

1. Copy the skill to your personal skills directory:
   ```bash
   mkdir -p ~/.claude/skills
   cp -r .claude/skills/shortcuts ~/.claude/skills/
   ```

2. The skill will now be available in all your Claude Code sessions.

## Usage

Once installed, simply ask Claude to interact with your shortcuts. The skill will automatically activate when you mention shortcuts-related tasks.

### Example Commands

**List all available shortcuts:**
```
Show me all my shortcuts
```
or
```
List available shortcuts
```

**View a shortcut in the Shortcuts app:**
```
Open the "Morning Routine" shortcut
```
or
```
Show me the "Process Images" shortcut
```

**Run a shortcut:**
```
Run the "Convert to PDF" shortcut
```
or
```
Execute "Send Weekly Report" shortcut
```

**Run a shortcut with input:**
```
Run "Translate Text" shortcut with input "Hello World"
```
or
```
Process image.jpg using the "Resize Image" shortcut
```

## Requirements

- macOS 12 (Monterey) or later
- Claude Code CLI
- Shortcuts app (pre-installed on macOS)

## How It Works

This skill uses the macOS `shortcuts` command-line utility, which is built into macOS. The skill provides Claude with instructions on when and how to use the following commands:

- `shortcuts list` - Lists all shortcuts
- `shortcuts view "<name>"` - Opens a shortcut in the Shortcuts app
- `shortcuts run "<name>"` - Executes a shortcut

## Troubleshooting

### Shortcut not found
- Shortcut names are case-sensitive
- Make sure the shortcut exists in your Shortcuts app
- Try listing all shortcuts first to verify the exact name

### Permission issues
- Some shortcuts may require permissions (e.g., access to files, contacts, etc.)
- Grant necessary permissions when prompted by macOS

### Skill not activating
- Make sure the skill directory is in the correct location
- Verify the SKILL.md file has proper YAML frontmatter
- Try being more explicit in your request (mention "shortcuts" or "Shortcuts app")

## Examples

### Example 1: Finding and running a shortcut
```
User: What shortcuts do I have?
Claude: [Lists all shortcuts using 'shortcuts list']

User: Run the "Morning Routine" one
Claude: [Executes 'shortcuts run "Morning Routine"']
```

### Example 2: Processing a file with a shortcut
```
User: Use my "Optimize Image" shortcut to process photo.jpg
Claude: [Runs 'shortcuts run "Optimize Image" --input-path photo.jpg']
```

### Example 3: Inspecting a shortcut
```
User: Show me how the "Weekly Report" shortcut works
Claude: [Opens 'shortcuts view "Weekly Report"']
```

## Contributing

Contributions are welcome! Feel free to submit issues or pull requests to improve this skill.

## License

See the LICENSE file for details.

## Related Resources

- [Claude Code Documentation](https://docs.claude.com/claude-code)
- [Claude Code Skills Guide](https://docs.claude.com/en/docs/claude-code/skills.md)
- [macOS Shortcuts User Guide](https://support.apple.com/guide/shortcuts-mac)
