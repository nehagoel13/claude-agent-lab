# claude-agent-lab - Technical Documentation

## Architecture Overview

This repository is an experimental lab for exploring and developing Claude Code capabilities, including custom commands and skills.

### System Architecture
- **Type**: Claude Code experimental workspace
- **Structure**: Configuration-driven development environment
- **Key Components**:
  - Custom slash commands (.claude/commands/)
  - Reusable skills (.claude/skills/)
  - Project configuration (CLAUDE.md)

### Design Patterns
- **Skill-based architecture**: Modular, reusable AI capabilities defined as skills
- **Command-driven workflows**: Custom slash commands for common tasks
- **Documentation-as-code**: Skills that generate and maintain documentation

### Key Architectural Decisions
- Use `.claude/` directory for all Claude Code configurations
- Separate commands from skills for clarity
- Use markdown for all command and skill definitions

## Tech Stack

- **Platform**: Claude Code CLI
- **Configuration**: Markdown-based skill and command definitions
- **Version Control**: Git
- **Documentation Tools**: Pandoc (for HTML generation)

## Development Environment Setup

### Prerequisites
- Claude Code CLI installed
- Git
- Pandoc (optional, for HTML documentation generation)

### Installation Steps

```bash
# Clone repository
git clone [repository-url]
cd claude-agent-lab

# Verify Claude Code installation
claude --version

# The .claude directory is already configured
# Commands and skills are ready to use
```

### Configuration

#### CLAUDE.md
Project-level instructions that Claude Code reads automatically:
- Defines project context
- Sets behavioral rules (e.g., check docs/ folder)
- Provides guidelines for Claude

#### .claude/commands/
Custom slash commands that can be invoked in Claude Code:
- `generate-docs.md`: Generates comprehensive documentation

#### .claude/skills/
Reusable AI capabilities:
- `doc-developer/`: Developer documentation generation skill
- `doc-pm/`: Product manager documentation generation skill

## Project Structure

```
claude-agent-lab/
├── .claude/
│   ├── commands/
│   │   └── generate-docs.md       # Custom slash command
│   ├── skills/
│       ├── doc-developer/
│       │   ├── SKILL.md           # Skill entry point
│       │   └── SKILL_DOC_DEVELOPER.md  # Documentation guidelines
│       └── doc-pm/
│           ├── SKILL.md           # Skill entry point
│           └── SKILL_DOC_PM.md    # Documentation guidelines
├── CLAUDE.md                      # Project instructions
└── README.md                      # Project overview
```

### Directory Descriptions

- **`.claude/commands/`**: Contains markdown files defining custom slash commands
- **`.claude/skills/`**: Contains reusable skill modules with their own configurations
- **Root directory**: Project-level configuration and documentation

## Custom Commands

### /generate-docs

Generates comprehensive documentation for both developers and product managers.

**Usage:**
```bash
/generate-docs
```

**Process:**
1. Analyzes repository structure and git history
2. Generates DOCUMENTATION_DEVELOPER.md using doc-developer skill
3. Generates DOCUMENTATION_PM.md using doc-pm skill
4. Creates HTML versions using pandoc
5. Provides summary of generated documentation

**Output Files:**
- `DOCUMENTATION_DEVELOPER.md`: Technical documentation
- `DOCUMENTATION_PM.md`: Product documentation
- `DOCUMENTATION_DEVELOPER.html`: Portable HTML version (developer)
- `DOCUMENTATION_PM.html`: Portable HTML version (PM)

## Skills

### doc-developer

**Location**: `.claude/skills/doc-developer/`

**Purpose**: Generates technical documentation for software engineers.

**Key Features:**
- Analyzes codebase architecture
- Documents APIs, modules, and data flows
- Includes setup and deployment instructions
- Provides code examples and technical details

**Guidelines**: Defined in `SKILL_DOC_DEVELOPER.md`

**Invocation:**
- Directly via Skill tool
- Automatically via `/generate-docs` command

### doc-pm

**Location**: `.claude/skills/doc-pm/`

**Purpose**: Generates product documentation for product managers and stakeholders.

**Key Features:**
- Focuses on product features and capabilities
- Documents user-facing functionality
- Tracks releases and changes
- Non-technical, business-focused language

**Guidelines**: Defined in `SKILL_DOC_PM.md`

**Invocation:**
- Directly via Skill tool
- Automatically via `/generate-docs` command

## Development Workflow

### Creating a New Custom Command

1. **Create command file**:
```bash
# Create new command in .claude/commands/
touch .claude/commands/my-command.md
```

2. **Define command structure**:
```markdown
---
description: Brief description of what the command does
allowed-tools:
  - Read
  - Write
  - Bash
---

# Command Name

[Detailed instructions for Claude on how to execute this command]
```

3. **Test the command**:
```bash
# In Claude Code
/my-command
```

4. **Commit the command**:
```bash
git add .claude/commands/my-command.md
git commit -m "feat: add my-command custom command"
```

### Creating a New Skill

1. **Create skill directory**:
```bash
mkdir -p .claude/skills/my-skill
```

2. **Create SKILL.md entry point**:
```markdown
# My Skill

This skill [does something specific].

## Instructions

[Detailed instructions for Claude]

## Supporting Files
[List any additional files]
```

3. **Add supporting files** (optional):
```bash
touch .claude/skills/my-skill/SKILL_GUIDELINES.md
```

4. **Invoke the skill**:
- Use Skill tool in Claude Code
- Reference from a custom command

5. **Commit the skill**:
```bash
git add .claude/skills/my-skill/
git commit -m "feat: add my-skill"
```

### Git Workflow

```bash
# Create feature branch
git checkout -b feature/new-capability

# Make changes to commands or skills
# ...

# Commit changes
git add .
git commit -m "feat: add new capability"

# Push to remote
git push origin feature/new-capability

# Create pull request
# (Use GitHub web interface or gh CLI)
```

## Best Practices

### Command Design
- Keep commands focused on a single task
- Provide clear, step-by-step instructions
- Specify allowed tools to ensure proper permissions
- Include examples in the command description

### Skill Design
- Make skills reusable and composable
- Separate skill logic (SKILL.md) from guidelines (SKILL_*.md)
- Document skill inputs and outputs
- Preserve custom content with markers (e.g., `<!-- CUSTOM -->`)

### Documentation
- Keep CLAUDE.md up to date with project rules
- Document all custom commands and skills
- Use semantic commit messages
- Version documentation files alongside code

## Testing

### Manual Testing

```bash
# Test custom commands
/generate-docs

# Verify output files
ls -la DOCUMENTATION_*.md
ls -la DOCUMENTATION_*.html

# Review generated content
cat DOCUMENTATION_DEVELOPER.md
```

### Validation Checklist
- [ ] Custom commands execute without errors
- [ ] Skills produce expected output
- [ ] Generated documentation is accurate
- [ ] HTML versions render correctly
- [ ] Git history is clean and semantic

## Troubleshooting

### Command Not Found

**Problem**: Custom command doesn't work when invoked

**Solution**:
- Verify file exists: `ls -la .claude/commands/`
- Check file naming: Must be `.md` extension
- Restart Claude Code session
- Check for YAML frontmatter syntax errors

### Skill Execution Errors

**Problem**: Skill fails during execution

**Solution**:
- Check allowed-tools in command definition
- Verify skill files exist in `.claude/skills/`
- Review SKILL.md for proper markdown syntax
- Check Claude Code logs for detailed errors

### HTML Generation Fails

**Problem**: Pandoc fails to generate HTML files

**Solution**:
- Install pandoc: `brew install pandoc` (macOS)
- Verify pandoc installation: `pandoc --version`
- Check markdown syntax in source files
- Use `--self-contained` flag for portable HTML

### Git Conflicts

**Problem**: Merge conflicts in documentation files

**Solution**:
- Regenerate documentation using `/generate-docs`
- Preserve custom sections marked with `<!-- CUSTOM -->`
- Use `git diff` to understand changes
- Manually merge if needed

## Extending the Lab

### Ideas for New Commands
- `/code-review`: Automated code review command
- `/test`: Run project tests and analyze results
- `/deploy`: Deployment automation command
- `/analyze`: Codebase analysis and metrics

### Ideas for New Skills
- Code quality analyzer
- Test generator
- API documentation generator
- Changelog generator
- Performance profiler

### Integration Points
- GitHub Actions for automated documentation
- Pre-commit hooks for documentation validation
- CI/CD pipelines for skill testing
- Remote session sharing for collaboration

## References

- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [Custom Commands Guide](https://docs.anthropic.com/claude-code/commands)
- [Skills Documentation](https://docs.anthropic.com/claude-code/skills)
- [Git Best Practices](https://www.conventionalcommits.org/)

---

**Last Updated**: 2026-01-20
**Maintainer**: Repository owner
**Version**: 1.0.0
