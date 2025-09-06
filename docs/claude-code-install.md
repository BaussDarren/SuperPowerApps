# CORRECT Claude Code Installation Guide for Windows

## Important: The Command is `claude` NOT `claude-code`!

Claude Code is installed via npm and runs with the command `claude` in your terminal.

---

## Prerequisites

You need **Node.js 18 or newer** installed. Let's check:

```powershell
# This checks if Node.js is installed and shows version
node --version

# This checks if npm is installed
npm --version
```

**If Node.js is NOT installed:**
- Download it from: https://nodejs.org/
- Choose the LTS version (recommended)
- Run the installer and restart your terminal

---

## Installation Steps

### Step 1: Install Claude Code via npm

```powershell
# This installs Claude Code globally on your system
# The @anthropic-ai scope is the official package
npm install -g @anthropic-ai/claude-code
```

**Note:** If you get permission errors, try:
```powershell
# Open PowerShell as Administrator and run:
npm install -g @anthropic-ai/claude-code
```

### Step 2: Verify Installation

```powershell
# This should show Claude Code version if installed correctly
claude --version
```

### Step 3: Start Claude Code

```powershell
# Navigate to your project directory first
cd C:\Users\bauss\src\super-power-apps

# Start Claude Code - it will prompt for login on first use
claude
```

### Step 4: Login Options

When you run `claude` for the first time, you'll be prompted to choose a login method:

1. **Claude.ai Account (Pro or Max Plan)** - If you have a paid Claude subscription
   - Uses your existing Claude Pro ($20/month) or Max ($100-200/month) subscription
   - Best for general usage

2. **Anthropic Console Account** - For API usage
   - Requires an API key from: https://console.anthropic.com/settings/keys
   - Uses pay-as-you-go API pricing
   - Best for developers who want direct API access

The login will open a browser window for authentication.

---

## Alternative Installation Methods

### Using Windows Package Installer (Alternative)

```powershell
# This downloads and runs the Windows installer script
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd

# For a specific version
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd 1.0.58 && del install.cmd
```

---

## Using Claude Code - Commands

Once installed and logged in, here's how to use Claude Code:

### Basic Commands

```powershell
# Start interactive session in current directory
claude

# Start with an initial prompt
claude "explain this codebase structure"

# Direct mode - get answer and exit
claude -p "write a function to calculate factorial"
```

### Inside Interactive Mode - Slash Commands

When you're in an interactive session, you can use these commands:

```
/help          # Show all available commands
/clear         # Clear context and start fresh
/model         # Switch between models (Sonnet 4 or Opus 4)
/status        # Check usage limits
/logout        # Log out of Claude Code
/login         # Switch accounts
/bug           # Report a bug
/quit          # Exit Claude Code
```

### Working with Code

```powershell
# Have Claude explain your code
"Can you explain what this function does?"

# Generate new code
"Create a REST API endpoint for user authentication"

# Debug issues
"I'm getting this error: [paste error]. How do I fix it?"

# Refactor code
"Can you refactor this function to be more efficient?"

# Write tests
"Write unit tests for the UserService class"
```

### File Operations

Claude Code can:
- Read files in your project directory automatically
- Edit files (asks for permission first)
- Create new files
- Run commands (with permission)

Example workflow:
```
You: "Create a new React component for a login form"
Claude: [Shows the code and asks to create LoginForm.jsx]
You: [Approve]
Claude: [Creates the file]
```

---

## Troubleshooting

### If `claude` command not found after installation:

```powershell
# 1. Check if it's installed
npm list -g @anthropic-ai/claude-code

# 2. Find where npm installs global packages
npm config get prefix

# 3. Make sure that path is in your PATH environment variable
echo $env:PATH

# 4. Try reinstalling
npm uninstall -g @anthropic-ai/claude-code
npm install -g @anthropic-ai/claude-code

# 5. Restart your terminal completely
```

### If you get permission errors:

```powershell
# Option 1: Run PowerShell as Administrator

# Option 2: Change npm's default directory
npm config set prefix "$env:USERPROFILE\.npm-global"
# Then add $env:USERPROFILE\.npm-global to your PATH

# Option 3: Use npx instead of global install
npx @anthropic-ai/claude-code
```

### Check your Node/npm setup:

```powershell
# Run diagnostic
npm doctor

# Clear npm cache if having issues
npm cache clean --force
```

---

## Costs and Limits

### With Claude Pro/Max Subscription:
- **Pro ($20/month)**: Good for light coding on small repos
- **Max 5x ($100/month)**: 50-200 prompts every 5 hours
- **Max 20x ($200/month)**: 200-800 prompts every 5 hours

### With Anthropic Console (API):
- Pay per token at standard API rates
- Check pricing: https://www.anthropic.com/pricing

---

## Important Links

- **Claude Code Documentation:** https://docs.anthropic.com/en/docs/claude-code
- **Get API Key (if using Console):** https://console.anthropic.com/settings/keys
- **Claude Subscription Plans:** https://claude.ai/upgrade
- **Support:** https://support.anthropic.com

---

## Tips for Effective Use

1. **Clear context between tasks**: Use `/clear` to reset when switching between different problems
2. **Be specific**: "Fix the login bug" → "The login form doesn't validate email format correctly"
3. **Use markdown files as scratchpads**: For complex tasks, have Claude write progress to a .md file
4. **Check `/status` regularly**: Monitor your usage limits
5. **Use the right model**: Sonnet 4 for everyday tasks, Opus 4 for complex problems

---

## Quick Reference Card

| What You Want | Command/Prompt |
|--------------|----------------|
| Start Claude | `claude` |
| Get help | `/help` |
| Clear context | `/clear` |
| Check limits | `/status` |
| Switch model | `/model` |
| Exit | `/quit` or Ctrl+C |
| Generate code | "Create a [description]" |
| Debug | "This error occurs: [error]" |
| Explain code | "Explain this function" |
| Refactor | "Refactor this for better performance" |