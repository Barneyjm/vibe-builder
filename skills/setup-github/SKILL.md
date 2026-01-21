---
name: setup-github
description: Help set up a GitHub account and CLI authentication. Use this when someone needs to create or configure their GitHub account.
---

# GitHub Setup Guide

You are helping someone set up GitHub from scratch. Be patient and thorough.

## Step 1: Create GitHub Account (if needed)

Ask if they already have a GitHub account. If not:

1. Open the signup page in their browser:
   - macOS: `open https://github.com/signup`
   - Linux: `xdg-open https://github.com/signup`
   - Windows: `start "" "https://github.com/signup"`

2. Guide them through signup:
   - "Enter your email address"
   - "Create a strong password"
   - "Choose a username (this will be public, like @username)"
   - "Complete the verification puzzle"
   - "Check your email for the verification code"

3. Wait for them to confirm they're signed up

## Step 2: Install GitHub CLI

Check if `gh` is installed by running `gh --version`. If not installed:

**macOS (with Homebrew):**
```bash
brew install gh
```

**macOS (without Homebrew):**
First check if Homebrew is available. If not, offer to install it:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**Linux (Debian/Ubuntu):**
```bash
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```

**Linux (Fedora):**
```bash
sudo dnf install gh
```

**Windows:**
```powershell
winget install --id GitHub.cli
```

Or direct them to: https://github.com/cli/cli#installation

## Step 3: Authenticate with GitHub

Run the authentication flow:

```bash
gh auth login
```

Guide them through the prompts:
1. "What account do you want to log into?" → **GitHub.com**
2. "What is your preferred protocol?" → **HTTPS** (simpler for beginners)
3. "Authenticate Git with your GitHub credentials?" → **Yes**
4. "How would you like to authenticate?" → **Login with a web browser**

Then:
1. They'll see a one-time code
2. A browser will open to https://github.com/login/device
3. They enter the code
4. Click "Authorize"
5. Come back to the terminal

## Step 4: Verify Setup

Run these commands to verify everything works:

```bash
gh auth status
```

This should show they're logged in. Also verify git is configured:

```bash
git config --global user.name
git config --global user.email
```

If these aren't set, help them configure:

```bash
git config --global user.name "Their Name"
git config --global user.email "their-email@example.com"
```

## Success Message

Once complete, congratulate them! They now have:
- A GitHub account to store and share their code
- The GitHub CLI for easy repository management
- Git configured and ready to track their projects

Let them know they can now create repositories, collaborate with others, and back up their code to the cloud.
