---
name: deploy
description: Set up automatic deployments by connecting your GitHub repo to Vercel. Push = deploy with zero configuration.
---

# Set Up Automatic Deployments

You are helping someone connect their GitHub repo to Vercel so that **pushing code = deploying their site**. This uses Vercel's native GitHub integration - no secrets or config files needed.

## The Goal

After this setup:
- `git push` → Site automatically updates
- No secrets to manage
- No workflow files to maintain
- Pull requests get preview URLs automatically

## Prerequisites Check

```bash
# Check Vercel CLI
vercel --version

# Check GitHub CLI
gh --version

# Check if in a git repo
git status
```

If anything is missing, help them install it first.

## Step 1: Create GitHub Repository

If they don't have a GitHub repo yet:

```bash
PROJECT_NAME=$(basename $(pwd))
gh repo create $PROJECT_NAME --public --source=. --push
```

If they want it private, use `--private` instead.

## Step 2: Deploy to Vercel

Create the Vercel project and deploy automatically:

```bash
vercel --yes
```

This creates the project, builds it, and deploys - all with one command. They'll see a live URL at the end!

**Explain**: "Your site is now live on Vercel! But we still need to connect it to GitHub for automatic deployments."

## Step 3: Link GitHub for Auto-Deploy

If Vercel didn't automatically prompt to connect GitHub, open the project settings:

```bash
# Get the project URL
vercel project ls
```

Then open the Vercel dashboard:
- macOS: `open https://vercel.com/dashboard`
- Linux: `xdg-open https://vercel.com/dashboard`
- Windows: `start "" "https://vercel.com/dashboard"`

Guide them:
1. Click on their project
2. Go to **Settings** → **Git**
3. Click **Connect Git Repository**
4. Select **GitHub**
5. Authorize Vercel (if not already)
6. Select their repository
7. Click **Connect**

**Explain**: "This links your GitHub repo to Vercel. Now whenever you push code, Vercel automatically rebuilds and deploys your site."

## Step 4: Verify It Works

Make a small test change, then:

```bash
git add .
git commit -m "Test automatic deployment"
git push
```

Open the Vercel dashboard or run:
```bash
vercel ls
```

They should see a new deployment in progress!

**Explain**: "See? You just pushed code and Vercel is already deploying it. No extra commands needed."

## That's It!

They now have:
- **Automatic deployments** - Push to main → site updates
- **Preview deployments** - Every PR gets its own URL
- **Zero maintenance** - No tokens to rotate, no workflows to update

## The Simple Workflow

From now on:

```bash
# Make changes, then:
git add .
git commit -m "What you changed"
git push
# Done! Site updates automatically.
```

## Troubleshooting

**Vercel not detecting pushes?**
- Check Settings → Git in Vercel dashboard
- Make sure the repo is connected
- Try disconnecting and reconnecting

**Wrong branch deploying?**
- Vercel deploys the default branch (usually `main`)
- Can change in Settings → Git → Production Branch

**Build failing?**
- Check the deployment logs in Vercel dashboard
- Usually a missing dependency or build error
