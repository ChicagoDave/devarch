# DevArch

Software development and architecture guidance for the modern era — where AI is your pair programming partner.

## About

This repository contains practical guidance for software developers and architects, with a particular focus on effective workflows when collaborating with generative AI tools like Claude Code, GitHub Copilot, and similar assistants.

The patterns here emerged from real-world project experience, not theory. They address the actual challenges developers face when integrating AI into their daily workflow.

## Why This Exists

AI-assisted development is powerful but introduces new challenges:

- **Context limitations** — AI tools have finite memory and lose context
- **Session continuity** — Work spans multiple sessions; AI doesn't remember
- **Decision traceability** — "Why did we do it this way?" gets lost
- **Knowledge transfer** — Onboarding AI to your codebase takes effort

Traditional development practices don't fully address these issues. This repo provides patterns that do.

## Contents

### Workflow Guides

Choose the guide that matches your tooling:

| Tool / Environment | Guide | Best For |
|--------------------|-------|----------|
| **Claude Code CLI** | [Claude Code Workflow Guide](docs/claude-code-workflow-guide.md) | Terminal-first development, automatic hooks, integrated workflow |
| **GitHub Copilot + Visual Studio 2026** | [Copilot Workflow Guide](docs/copilot-workflow-guide.md) | Windows development, .NET/C# projects, Azure DevOps integration |

Both workflows provide **100% functional equivalence** — same patterns, same results, different tools.

### Additional Guides

| Guide | Description |
|-------|-------------|
| [AWS Serverless Backend Guide](docs/aws-serverless-backend-guide.md) | Let AI build your API: Lambda, API Gateway, DynamoDB, custom domains, hardening |
| [Architecture Decision Records](docs/architecture-decision-records-guide.md) | When and how to document design decisions with ADRs |

### Key Topics Covered

- **Context management** — Strategies for working within AI context limits
- **Session summaries** — Maintaining continuity across sessions
- **Work documentation** — Patterns for preserving decisions and progress
- **Project organization** — Folder structures that work with AI tools
- **Hooks and automation** — Reducing manual overhead

## Quick Start

### For Claude Code CLI Users

```bash
# Clone and start
git clone https://github.com/SangeetAgarwal/devarch.git
cd devarch

# Read the guide
cat docs/claude-code-workflow-guide.md

# Set up hooks (optional)
# See guide for .claude/settings.json configuration
```

### For GitHub Copilot + Visual Studio 2026 Users

```powershell
# Clone repository
git clone https://github.com/SangeetAgarwal/devarch.git
cd devarch

# Create a new feature
.\scripts\New-Feature.ps1 -FeatureName "your-feature"

# Read the comprehensive guide
code docs\copilot-workflow-guide.md

# See all available scripts
Get-ChildItem .\scripts\*.ps1
```

**Prerequisites:**
- PowerShell 5.1+ (pre-installed on Windows)
- Git
- Visual Studio 2026 with GitHub Copilot extensions
- Claude Opus 4.5 model (select in Copilot settings)

## Philosophy

1. **Documentation is memory** — What you write down survives; what stays in AI context doesn't
2. **Progressive capture** — Document as you go, not at the end
3. **Branch = Work folder** — Keep related artifacts together
4. **Explicit over implicit** — AI works better with clear structure and instructions

## Dual Workflow Approach

This repository supports two complementary workflows:

### Claude Code CLI Workflow
- **Automation**: Automatic hooks for session management
- **Integration**: Native CLI commands (`write work summary`, `/context`)
- **Best for**: Terminal-based development, quick automation

### GitHub Copilot + Visual Studio Workflow
- **Automation**: PowerShell scripts for session management
- **Integration**: Visual Studio 2026, Azure DevOps pipelines
- **Best for**: Windows development, .NET ecosystem, enterprise environments

**Both workflows share the same core principles:**
- Session summaries for context continuity
- Work folders matching branches
- ADRs for architectural decisions
- Implementation plans for progress tracking
- Progressive documentation throughout development

## Contributing

Found a pattern that works well? Have improvements to suggest? Contributions are welcome.

## License

MIT

---

*These patterns evolved from building [Sharpee](https://github.com/ChicagoDave/sharpee), a parser-based interactive fiction engine, using AI-assisted development.*
