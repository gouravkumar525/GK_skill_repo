# Skill: nodejs-install

Guide the user through checking for an existing Node.js installation and installing Node.js 24 if needed, on macOS or Windows.

## Trigger

Invoke this skill when the user asks to install Node.js, npm, or mentions errors like `node: command not found` or `npm: command not found`.

---

## Step 1 — Pre-install Validation

Before installing anything, check whether Node.js and npm are already present.

**Run these commands:**
```
node -v
npm -v
npx -v
```

**Interpret the output:**

| Result | Action |
|--------|--------|
| `node -v` returns `v24.x.x` and `npm -v` returns `11.x.x` | Already installed and up to date — skip to Post-install Validation to confirm everything works |
| `node -v` returns an older version (e.g. `v18`, `v20`) | Upgrade using the steps below |
| `command not found` / `'node' is not recognized` | Not installed — proceed with installation |

If the user is already on Node.js 24 and npm 11, skip to **Step 3** and just run the validation checks.

---

## Step 2 — Installation

### macOS — via nvm (recommended)

nvm lets you manage multiple Node versions without `sudo`.

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash

# Load nvm in the current shell (no restart needed)
\. "$HOME/.nvm/nvm.sh"

# Install Node.js 24 (npm is bundled — no separate install needed)
nvm install 24
```

> **Note:** npm is included with Node.js. You do not need to install it separately.

**Troubleshooting — macOS:**

| Problem | Fix |
|---------|-----|
| `curl: command not found` | Install Xcode CLI tools: `xcode-select --install` |
| `nvm: command not found` after install | Run `. "$HOME/.nvm/nvm.sh"` or open a new terminal tab |
| `node` still not found after `nvm install` | Run `nvm use 24` to activate the installed version |
| Permission denied errors | Do **not** use `sudo` with nvm — it manages per-user installs |
| nvm missing from new terminal sessions | Add `. "$HOME/.nvm/nvm.sh"` to `~/.zshrc` or `~/.bash_profile` |

---

### Windows — via Chocolatey

```powershell
# Install Chocolatey (run in an elevated PowerShell — right-click → Run as Administrator)
powershell -c "irm https://community.chocolatey.org/install.ps1 | iex"

# Install Node.js 24 (npm is bundled — no separate install needed)
choco install nodejs --version="24.15.0"
```

> **Note:** npm is included with Node.js. You do not need to install it separately.

**Troubleshooting — Windows:**

| Problem | Fix |
|---------|-----|
| `choco: command not found` after install | Close and reopen PowerShell as Administrator |
| `execution of scripts is disabled` | Run: `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser` |
| `node` not found after choco install | Restart terminal; if still missing, check `C:\Program Files\nodejs` is on PATH |
| Version conflict with existing Node | Run `choco upgrade nodejs --version="24.15.0"` instead of install |
| `npm` errors after install | Restart terminal to pick up updated PATH |

---

## Step 3 — Post-install Validation

Run all four checks to confirm the installation is working correctly:

```
node -v
```
Expected: `v24.15.0`

```
npm -v
```
Expected: `11.12.1`

```
npx -v
```
Expected: a version number (same as npm)

```
node -e "console.log('Node is working!')"
```
Expected: `Node is working!`

If all four pass, Node.js is ready to use.

---

## Platform Comparison

| | macOS (nvm) | Windows (Chocolatey) |
|--|-------------|----------------------|
| **Tool** | nvm | Chocolatey |
| **Requires admin** | No | Yes (elevated PowerShell) |
| **Multiple versions** | Yes (`nvm use <version>`) | Possible but manual |
| **npm included** | Yes | Yes |
| **After install** | `. "$HOME/.nvm/nvm.sh"` or new terminal | New terminal or restart |
| **Upgrade Node** | `nvm install <version>` | `choco upgrade nodejs` |
