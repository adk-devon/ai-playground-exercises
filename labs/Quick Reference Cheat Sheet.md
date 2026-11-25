# GitHub Copilot for VS Code: Quick Reference Cheat Sheet

## Essential Keyboard Shortcuts (Windows)

### Code Suggestions
| Action | Shortcut | Description |
|--------|----------|-------------|
| **Accept Suggestion** | `Tab` | Accept the current Copilot suggestion |
| **Reject Suggestion** | `Esc` | Dismiss the current suggestion |
| **Next Suggestion** | `Alt + ]` | Cycle to the next alternative suggestion |
| **Previous Suggestion** | `Alt + [` | Cycle to the previous alternative suggestion |
| **Trigger Suggestion** | `Ctrl + Space` | Manually trigger Copilot suggestions |
| **Accept Word** | `Ctrl + →` | Accept only the next word of the suggestion |
| **Accept Line** | `Ctrl + Enter` | Accept only the current line of the suggestion |

### Copilot Chat
| Action | Shortcut | Description |
|--------|----------|-------------|
| **Open Chat View** | `Ctrl + Alt + I` | Open Copilot Chat panel in sidebar |
| **Inline Chat** | `Ctrl + I` | Open inline chat in editor |
| **Voice Chat** | `Ctrl + I` (hold) | Start voice conversation with Copilot |
| **New Chat Session** | `Ctrl + N` | Start new chat session in Chat view |
| **Agent Mode** | `Ctrl + Shift + I` | Switch to agent mode |

**Reference:** [GitHub Copilot in VS Code Features](https://code.visualstudio.com/docs/copilot/reference/copilot-vscode-features)

---

## Copilot Chat Commands & Variables

### Chat Variables (Use # to reference context)
| Variable | Description | Example |
|---------|-------------|---------|
| `#file` | Include current file's content | `#file explain this function` |
| `#selection` | Include currently selected text | `#selection optimize this code` |
| `#function` | Include current function/method | `#function add error handling` |
| `#class` | Include current class | `#class explain this design pattern` |
| `#line` | Include current line of code | `#line fix this syntax error` |
| `#project` | Include project context | `#project show me all API routes` |
| `#sym` | Include current symbol | `#sym explain this variable` |
| `#block` | Include current block of code | `#block what does this do?` |
| `#path` | Include file path | `#path where is this file located?` |
| `#comment` | Include current comment | `#comment explain this TODO` |

### Slash Commands (Official VS Code commands)
| Command | Description | Example |
|---------|-------------|---------|
| `/clear` | Start a new chat session | `/clear` |
| `/explain` | Explain how code works | `/explain how does this algorithm work?` |
| `/fix` | Propose fixes for problems | `/fix this function has a bug` |
| `/tests` | Generate unit tests | `/tests create tests for this function` |
| `/new` | Create a new project | `/new create a React app` |
| `/help` | Quick reference for Copilot | `/help` |
| `/fixTestFailure` | Find and fix failing tests | `/fixTestFailure why is this test breaking?` |

**Reference:** [GitHub Copilot Chat Cheat Sheet](https://docs.github.com/en/copilot/reference/cheat-sheet)

---

## Chat Participants & Agents

### Chat Participants (Official agents)
| Agent | Command | Description |
|-------|---------|-------------|
| **Workspace** | `@workspace` | Ask questions about your codebase structure and patterns | 
| **VSCode** | `@vscode` | Get help with VS Code features and settings |
| **Terminal** | `@terminal` | Get help with terminal/command line tasks |
| **GitHub** | `@github` | Access GitHub-specific skills and repository information |

### Chat Participant Examples
```
@workspace how do I add authentication to this app?
@workspace find all TODO comments in my project
@vscode how do I set up debugging for Node.js?
@terminal how do I create a git branch?
@github what issues are assigned to me?
```

**Reference:** [Using GitHub Copilot Chat Participants](https://docs.github.com/en/copilot/how-tos/chat/asking-github-copilot-questions-in-your-ide)

---

## Status Bar Indicators

### Copilot Status Icons
| Icon | Meaning |
|------|---------|
| 🤖 **Active** | Copilot is active and ready |
| ⏸️ **Paused** | Suggestions are paused |
| ❌ **Disabled** | Copilot is disabled for this file type |
| ⚠️ **Warning** | Authentication or connection issue |

**Reference:** [Configuring GitHub Copilot in VS Code](https://docs.github.com/en/copilot/how-tos/configure-personal-settings/configure-in-your-environment)

---

## Chat Modes

### Available Chat Modes
| Mode | Description | Best For |
|------|-------------|----------|
| **Ask** | Get answers and code suggestions | Questions about code, explanations, general help |
| **Edit** | Make changes across multiple files | Coordinated edits, refactoring across project |
| **Agent** | Autonomous multi-step workflows | Complex tasks, feature implementation |

### How to Switch Modes
- Use the dropdown at the top of the Chat view
- Or use `Ctrl + Shift + I` to switch to Agent mode directly

**Reference:** [Using Chat in VS Code](https://code.visualstudio.com/docs/copilot/chat/copilot-chat)

---

## Prompt Files & Customization

### Copilot Instructions File
**File:** `.github/copilot-instructions.md`
**Purpose:** Global instructions that apply to all Copilot interactions in your project
**Usage:** Automatically included in every chat request

```markdown
# Project: E-commerce Platform
Use TypeScript for all new code.
Follow our coding standards: camelCase, descriptive names.
Include error handling and JSDoc comments.
Prefer async/await over promises.
```

### Custom Prompt Files
**Location:** `.github/prompts/`
**Extension:** `.prompt.md`
**Purpose:** Reusable prompts for common tasks
**Usage:** Reference with `#prompt:filename`

#### Example: Code Review Prompt
**File:** `.github/prompts/code-review.prompt.md`
```markdown
Review this code for:
- Security vulnerabilities
- Performance issues  
- Code style consistency
- Best practices adherence
- Documentation completeness
```

#### Example: API Development Prompt
**File:** `.github/prompts/api-development.prompt.md`
```markdown
Create a REST API endpoint that:
- Follows RESTful conventions
- Includes proper error handling
- Has input validation
- Returns appropriate HTTP status codes
- Includes OpenAPI documentation
```

### Chat Mode Files
**Location:** `.github/copilot-chat-modes/`
**Extension:** `.md`
**Purpose:** Define specialized chat behaviors and tool access
**Usage:** Select from chat mode dropdown

#### Example: Code Reviewer Mode
**File:** `.github/copilot-chat-modes/code-reviewer.md`
```markdown
---
description: 'Review code for quality and adherence to best practices.'
tools: ['codebase', 'usages', 'vscodeAPI', 'problems']
---
# Code Reviewer Mode
You are a senior developer conducting thorough code reviews.
Focus on code quality, security, and maintainability.
```

### Language-Specific Instructions
**Purpose:** Provide language-specific guidance for better code generation
**Usage:** Automatically applied when working in specific languages

#### Example: JavaScript Instructions
```markdown
# JavaScript Guidelines
- Use ES6+ features (arrow functions, destructuring, modules)
- Prefer const/let over var
- Use template literals for string interpolation
- Include proper error handling with try/catch
```

### How to Use Prompt Files
| Action | Command | Example |
|--------|---------|---------|
| **Reference Prompt File** | `#prompt:filename` | `#prompt:code-review check this function` |
| **Add Context** | Click ➕ in chat input | Select prompt file from context menu |
| **Create New Prompt** | Save `.prompt.md` in `.github/prompts/` | Custom prompts appear in `#prompt:` suggestions |

**Reference:** [Customize Chat Responses in VS Code](https://learn.microsoft.com/en-us/visualstudio/ide/copilot-chat-context)

---

## Latest VS Code Copilot Features (2026 Update)

> Features and availability can vary by VS Code build, account, model, agent harness, and organization policy. Always review generated changes before accepting them.

### Beginner Quick Start

| What you want | Where to start | Example |
|---------------|----------------|---------|
| Explain code without changing it | **Ask** agent | `Where is sign-in validation implemented?` |
| Plan before implementation | **Plan** agent or `/plan` | `/plan Add pagination without breaking existing API clients` |
| Implement and validate a change | **Agent** agent | `Fix the failing test, add a regression test, and run the relevant tests.` |
| Change only selected code | Inline Chat: `Ctrl + I` | `Handle empty input without changing other behavior.` |
| Add code as you type | Inline suggestion | Accept with `Tab`; dismiss with `Esc` |
| Ask for the right action | Type `/` in chat | Choose `/plan`, `/compact`, `/fork`, or an installed skill |

### Current Agent Workflow

| Built-in agent | Purpose | Best for |
|----------------|---------|----------|
| **Ask** | Read-only questions and codebase research | Understanding code, tracing behavior, answering questions |
| **Plan** | Researches and proposes an implementation plan | Reviewing scope, files, tests, risks, and open decisions |
| **Agent** | Uses tools to edit, run commands, and validate | Feature implementation, bug fixes, test-driven changes |

Use the **Session Target** control to choose a harness. **Copilot** is the recommended default for most day-to-day tasks. Other available targets can include Claude, Codex, Local, or Cloud, depending on your setup.

> **Local harness note:** The Local harness is deprecated and is scheduled for removal in February 2027. Move reusable workflows to Agent Skills or the Copilot harness.

### Model, Harness, and Execution Controls

| Control | Purpose |
|---------|---------|
| **Agent picker** | Switch among Ask, Plan, Agent, and custom agents |
| **Model picker** | Choose an available model based on quality, speed, and cost |
| **Session Target** | Choose Copilot, Claude, Codex, Local, or Cloud execution |
| **Permissions** | Control confirmation behavior for file edits and commands |
| **Autopilot** | Experimental higher-autonomy operation with automatic approvals where allowed |
| **Agents window** | Coordinate independent sessions across folders or repositories |

Changing the model does not change the harness. For example, selecting a Claude model in a Copilot session still uses the Copilot harness.

### Better Context in Chat

Use the `+` / **Add Context** menu or type `#` to attach exactly what Copilot should use.

| Context | How to use it |
|---------|---------------|
| Files and folders | `#file`, `#folder`, or Add Context |
| Code symbols | `#symbol` or select a symbol |
| Workspace search | `#codebase` searches relevant workspace code |
| Terminal selection/output | `#terminalSelection` or `#terminalLastCommand` where available |
| Source Control changes | Attach changes or use Source Control context |
| GitHub issue or pull request | Paste its URL or select Issue/Pull Request |
| Web content | Paste a URL or mention `#fetch` to retrieve external documentation |
| Images and screenshots | Drag/drop an image or use Add Context > Screenshot Window/App Window |
| Browser elements | Add HTML, CSS, and screenshot context from the integrated browser |

Add context explicitly when the correct source matters; opening or mentioning a file does not guarantee that the model sees its entire contents.

### Advanced Chat Shortcuts and Slash Commands

| Command or action | Purpose |
|-------------------|---------|
| `/plan <task>` | Research a task and produce a plan before changing code |
| `/compact` | Summarize earlier conversation context |
| `/fork` | Copy the conversation history to explore another approach |
| `/automate` | Turn a task or idea into a recurring automation in the Agents window |
| `/<skill-name>` | Run an installed Agent Skill as a slash command |
| `!npm test` | Run a terminal command directly from chat; first character must be `!` |
| Send while a request is running | Choose **Add to Queue**, **Steer with Message**, or **Stop and Send** |
| Restore checkpoint | Restore affected files and chat history from an earlier point |

`!` commands depend on the harness and execution target. They are not available in every Local, Cloud, or extension-based session.

### Review, Permissions, and Safe Recovery

| Situation | Recommended action |
|-----------|--------------------|
| Start work on an existing project | Use **Manual permissions** for the first task |
| Review pending edits | In the Chat view, open each changed file and use **Keep** or **Undo** |
| Review diffs across a larger task | Use the Agents window **Changes** view |
| Agent is heading in the wrong direction | **Steer with Message** or **Stop and Send** |
| Restore local file changes and chat history | Use **Restore Checkpoint** |
| Restrict terminal access | Configure agent sandboxing |
| Keep execution off the local machine | Use a remote host or managed cloud session |

Stopping or restoring a checkpoint does not undo terminal commands or changes already made to external services. Review diffs and test results before committing.

### Customize Copilot for a Project

Use the **Chat: Open Customizations** command to manage instructions, agents, prompts, skills, plugins, and MCP servers.

| Customization | File or location | When to use it |
|---------------|------------------|----------------|
| Project instructions | `.github/copilot-instructions.md` or `AGENTS.md` | Shared project conventions and repeated rules |
| Targeted instructions | `.github/instructions/*.instructions.md` | Rules for matching file types or folders |
| Agent Skills | `.github/skills/<skill-name>/SKILL.md` or profile/user locations | Reusable, on-demand workflows with instructions, scripts, templates, or examples |
| Custom agents | `.github/agents/*.agent.md` | Reusable roles with a specific purpose, tool set, and output format |
| Prompt files (Local only) | `.github/prompts/*.prompt.md` | Invoke a reusable prompt by `/name` in a Local harness session |
| MCP servers | VS Code MCP configuration | Give agents tools and data sources such as databases or documentation |
| Plugins | Customization Marketplace | Install bundled instructions, agents, skills, MCP tools, or integrations |

#### Targeted instruction example

```markdown
---
applyTo: 'tests/**/*.py'
---
# Python test instructions
- Reuse fixtures from `tests/conftest.py`.
- Name tests `test_<behavior>_<condition>`.
- Run `python -m pytest <test-file>` after changing a test.
```

#### Custom agent example

```markdown
---
name: Reviewer
description: Review code for incorrect behavior and missing tests without editing files
tools: ['read', 'search']
---
Review the supplied code and report only actionable findings.
For each finding, include file and line, impact, and a suggested fix or test.
Do not edit files or run terminal commands.
```

For reusable workflows, prefer Agent Skills over prompt files for the Copilot harness. Local prompt files are being phased out because the Local harness is deprecated.

### MCP and External Tools

Use MCP when Copilot needs a tool or data source that is not already available.

1. Run **Chat: Open Customizations**.
2. Open **MCP Servers** and select **Add Server**.
3. Choose a supported URL/HTTP server or a local command.
4. Review the publisher, permissions, and sign-in requirements.
5. Give the agent a low-risk task and inspect each tool call.

Local MCP servers can execute code and use your account permissions. Approve only tools and actions you understand. Never place passwords or API keys in chat or shared configuration.

### Advanced Delegation and Parallel Work

| Capability | How to use it |
|------------|---------------|
| **Agents window** | Start and coordinate multiple independent coding sessions |
| **Custom agents as subagents** | Delegate specialized read-only or implementation tasks |
| **Worktrees** | Isolate agent edits from your active working tree |
| **Cloud sessions** | Run interactive agent work without keeping the local machine online |
| **GitHub environments** | Continue supported agent sessions across VS Code, GitHub, and Copilot apps |
| `/fork` | Explore another approach while retaining the conversation history |
| Mixed-harness session | Start a separate conversation using another agent harness |

Forking a conversation does not isolate file changes. Use a worktree or separate session when changes must be kept independent.

### Visual Responses and Image Features

The Agents window can produce visual responses for reports, diagrams, mockups, and static UI previews.

| Feature | Example |
|---------|---------|
| `/html-preview` | `/html-preview compare the two caching approaches in a visual report` |
| `/vscode-ui` | `/vscode-ui compare build times in a table and bar chart` |
| Image attachment | Attach a screenshot or UI mockup and describe the requested change |
| Image generation | Experimental: ask an image-capable Copilot harness to generate or edit an asset |
| Mark Up | Annotate an attached image with arrows, shapes, text, or a crop |

HTML previews are static and do not support scripts, forms, external links, or external resources. Native UI visual components and image generation can be experimental and setting-dependent.

### Beginner vs. Advanced Usage

**Beginners**
- Ask Copilot to explain code before asking it to edit code.
- Start in **Ask**, then move to **Plan**, then use **Agent**.
- Attach only the relevant files and errors.
- Review every diff and run tests.
- Use `/plan` for unfamiliar or high-impact changes.

**Advanced users**
- Split responsibilities across project instructions, targeted instructions, skills, custom agents, and MCP.
- Use subagents or the Agents window for independent workstreams.
- Use worktrees to isolate larger changes.
- Set permissions and sandbox limits appropriate to the project.
- Fork sessions to compare approaches, but verify changes independently.
- Add repeatable validation commands to instructions or Agent Skills.

**Recommended prompt structure**

```text
Goal:
<what outcome you need>

Context:
<relevant files, symbols, errors, or constraints>

Requirements:
<behavior, compatibility, style, security, or performance constraints>

Verification:
<tests or checks Copilot should run>
```

**Official References**
- [AI features cheat sheet](https://code.visualstudio.com/docs/agents/reference/ai-features-cheat-sheet)
- [Build with AI in VS Code](https://code.visualstudio.com/docs/agents/overview)
- [Use chat in VS Code](https://code.visualstudio.com/docs/chat/chat-overview)
- [Choose an agent harness](https://code.visualstudio.com/docs/agents/run/agent-harnesses)
- [Add context to chat](https://code.visualstudio.com/docs/chat/copilot-chat-context)
- [Custom instructions](https://code.visualstudio.com/docs/agent-customization/custom-instructions)
- [Agent Skills](https://code.visualstudio.com/docs/agent-customization/agent-skills)
- [Custom agents](https://code.visualstudio.com/docs/agent-customization/custom-agents)
- [MCP servers](https://code.visualstudio.com/docs/agent-customization/mcp-servers)

---

## Remember
- **Copilot is a tool, you're the developer** - Always review and understand generated code
- **Context is key** - The more context you provide, the better the suggestions
- **Experiment freely** - Try different prompting styles to see what works best
- **Stay curious** - Use Copilot to explore new patterns and approaches