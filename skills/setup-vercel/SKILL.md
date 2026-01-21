---
name: setup-vercel
description: Help set up a Vercel account and CLI authentication. Use this when someone needs to create or configure their Vercel account for deployments.
---

# Vercel Setup Guide

You are helping someone set up Vercel from scratch. Vercel makes deploying websites incredibly easy.

## Step 1: Create Vercel Account (if needed)

Ask if they already have a Vercel account. If not:

1. Open the signup page in their browser:
   - macOS: `open https://vercel.com/signup`
   - Linux: `xdg-open https://vercel.com/signup`
   - Windows: `start "" "https://vercel.com/signup"`

2. **Strongly recommend** signing up with GitHub:
   - Click "Continue with GitHub"
   - This links their accounts for seamless deployments
   - They won't need to configure anything extra

3. If they prefer email signup, that works too, but GitHub is easier

4. Wait for them to confirm they're signed up

## Step 2: Install Vercel CLI

Check if Node.js/npm is installed:
```bash
node --version
npm --version
```

If Node.js is not installed, help them install it:

**macOS (with Homebrew):**
```bash
brew install node
```

**Linux (using nvm - recommended):**
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
source ~/.bashrc  # or ~/.zshrc
nvm install --lts
```

**Windows:**
Direct them to: https://nodejs.org/ and download the LTS version

Once Node.js is ready, install Vercel CLI:

```bash
npm install -g vercel
```

Verify installation:
```bash
vercel --version
```

## Step 3: Authenticate with Vercel

Run the login command:

```bash
vercel login
```

Guide them through the options:
1. Choose their login method (GitHub is easiest if they signed up that way)
2. A browser will open for authentication
3. They authorize the CLI
4. Come back to the terminal

## Step 4: Verify Setup

Check that authentication worked:

```bash
vercel whoami
```

This should display their Vercel username.

## What Vercel Does (Brief Explanation)

Explain to them in simple terms:
- **Vercel hosts websites** - Their code goes on Vercel's servers
- **Automatic deployments** - Push to GitHub, site updates automatically
- **Free tier is generous** - Perfect for personal projects and learning
- **Zero configuration** - It figures out how to build most projects
- **Preview deployments** - Every branch gets its own URL to test

## Success Message

Once complete, congratulate them! They now have:
- A Vercel account ready to host their websites
- The Vercel CLI for deploying from the command line
- Connected to GitHub for automatic deployments (if they signed up with GitHub)

Let them know they can deploy unlimited projects on the free tier and their sites will be fast and secure out of the box.
