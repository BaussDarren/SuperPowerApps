# Claude Code Installation Guide for Windows

## ==== HERE ARE 3 WAYS TO INSTALL CLAUDE CODE ====

## Option 1: Direct Download (RECOMMENDED for Windows)

**What this does:** Downloads the pre-built Windows executable directly from Anthropic's releases.

1. **Download the Windows executable:**
   - Go to the Claude Code releases page: https://github.com/anthropics/claude-code/releases
   - Download the latest `claude-code-windows-amd64.exe` file
   - Rename it to `claude-code.exe` for convenience

2. **Add to your PATH:**
   
   **What this does:** Makes the `claude-code` command available from any directory in your terminal.
   
   ```powershell
   # Create a directory for CLI tools if you don't have one
   # This creates a folder in your user directory to store command-line tools
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\bin"
   
   # Move the downloaded exe to this directory
   # Replace YOUR_DOWNLOAD_PATH with your actual download location (usually C:\Users\YourName\Downloads)
   Move-Item -Path "YOUR_DOWNLOAD_PATH\claude-code.exe" -Destination "$env:USERPROFILE\bin\claude-code.exe"
   
   # Add the bin directory to your PATH for the current session
   # This makes the command available immediately
   $env:PATH = "$env:USERPROFILE\bin;$env:PATH"
   
   # Add to PATH permanently (requires admin privileges)
   # This ensures the command is available in future terminal sessions
   [Environment]::SetEnvironmentVariable("Path", "$env:USERPROFILE\bin;" + [Environment]::GetEnvironmentVariable("Path", "User"), "User")
   ```

3. **Set up your API key:**
   
   **What this does:** Authenticates you with the Anthropic API so Claude Code can make requests on your behalf.
   
   ```powershell
   # Set the API key for current session
   # Replace YOUR_API_KEY with your actual Anthropic API key
   $env:ANTHROPIC_API_KEY = "YOUR_API_KEY"
   
   # Set it permanently for your user
   [Environment]::SetEnvironmentVariable("ANTHROPIC_API_KEY", "YOUR_API_KEY", "User")
   ```
   
   **Get your API key here:** https://console.anthropic.com/settings/keys

4. **Verify installation:**
   
   ```powershell
   # This should display the Claude Code version
   claude-code --version
   ```

---

## Option 2: Using npm (if you have Node.js installed)

**What this does:** Installs Claude Code as a Node.js package globally on your system.

**Check if you have Node.js:**
```powershell
# This checks if Node.js is installed
node --version
```

If Node.js is installed:
```powershell
# Install Claude Code globally via npm
# The -g flag installs it system-wide rather than just for one project
npm install -g @anthropic/claude-code

# Set your API key (same as Option 1 step 3)
$env:ANTHROPIC_API_KEY = "YOUR_API_KEY"
[Environment]::SetEnvironmentVariable("ANTHROPIC_API_KEY", "YOUR_API_KEY", "User")

# Verify installation
claude-code --version
```

**Don't have Node.js?** Download it from: https://nodejs.org/

---

## Option 3: Using Chocolatey (Windows package manager)

**What this does:** Uses Chocolatey package manager to install and manage Claude Code.

**Check if you have Chocolatey:**
```powershell
# This checks if Chocolatey is installed
choco --version
```

If Chocolatey is installed:
```powershell
# Install Claude Code via Chocolatey
choco install claude-code

# Set your API key (same as Option 1 step 3)
$env:ANTHROPIC_API_KEY = "YOUR_API_KEY"
[Environment]::SetEnvironmentVariable("ANTHROPIC_API_KEY", "YOUR_API_KEY", "User")

# Verify installation
claude-code --version
```

**Don't have Chocolatey?** Install it from: https://chocolatey.org/install

---

## Using Claude Code

Once installed, you can use Claude Code like this:

```powershell
# Get help and see available commands
claude-code --help

# Generate code for a specific task
claude-code generate "Create a Python function to calculate fibonacci numbers"

# Debug existing code
claude-code debug yourfile.py

# Refactor code
claude-code refactor yourfile.js

# Ask Claude Code questions about your codebase
claude-code chat "How does the authentication system work in this project?"
```

## Troubleshooting

**If `claude-code` still isn't recognized after installation:**
1. Close and reopen your PowerShell window (to reload PATH)
2. Or run: `refreshenv` (if using Chocolatey)
3. Or manually restart Windows Terminal/PowerShell

**API Key issues:**
- Make sure your API key is valid: https://console.anthropic.com/settings/keys
- Check if the environment variable is set: `echo $env:ANTHROPIC_API_KEY`

**Need more help?**
- Claude Code documentation: https://docs.anthropic.com/en/docs/claude-code
- API documentation: https://docs.anthropic.com
- Support: https://support.anthropic.com