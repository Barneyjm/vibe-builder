---
name: deploy
description: Deploy a project to Vercel and optionally push to GitHub. Use this to get a project live on the internet.
---

# Deploy to the World

You are helping someone deploy their project to the internet. This is an exciting moment - their creation will be live!

## Prerequisites Check

First, verify they have what they need:

```bash
# Check if in a project directory
ls package.json

# Check if git is initialized
git status

# Check Vercel CLI
vercel --version

# Check GitHub CLI
gh --version
```

If anything is missing, help them set it up or direct them to the appropriate setup skill.

## Step 1: Commit Any Uncommitted Changes

Check for uncommitted work:

```bash
git status
```

If there are changes:

```bash
git add .
git commit -m "Ready for deployment"
```

## Step 2: Create GitHub Repository

Ask: "Do you want to push this to GitHub? (Recommended - it enables automatic deployments)"

If yes, create and push to GitHub:

```bash
# Get the project name from package.json or directory
PROJECT_NAME=$(basename $(pwd))

# Create the repository and push
gh repo create $PROJECT_NAME --public --source=. --push
```

**Explain**:
- "This creates a repository on GitHub and uploads your code"
- "Your code will be backed up and shareable"
- "Vercel can auto-deploy when you push changes"

If they prefer private: use `--private` instead of `--public`

## Step 3: Deploy to Vercel

Now the magic moment:

```bash
vercel --yes
```

**What happens:**
1. Vercel detects it's a Next.js project
2. Builds your application
3. Deploys to their global network
4. Gives you a URL

Wait for it to complete. You'll see output like:
```
✅ Production: https://project-name.vercel.app
```

## Step 4: Celebrate!

Open their new live website:

- macOS: `open https://PROJECT_NAME.vercel.app`
- Linux: `xdg-open https://PROJECT_NAME.vercel.app`
- Windows: `start https://PROJECT_NAME.vercel.app`

**This is huge!** They just deployed their first website. Make it feel special:

"Your website is LIVE on the internet! Anyone in the world can see it at [URL]. You did it!"

## Step 5: Connect GitHub for Auto-Deploy (if not already)

If they created a GitHub repo, help them connect it for automatic deployments:

1. Open Vercel dashboard:
   - macOS: `open https://vercel.com/dashboard`
   - Linux: `xdg-open https://vercel.com/dashboard`
   - Windows: `start https://vercel.com/dashboard`

2. Guide them:
   - Click on their project
   - Go to Settings → Git
   - Connect their GitHub repository
   - Now every `git push` will auto-deploy!

## Explain What They Have Now

Break down what just happened:

1. **Live Website**: Their code is running on Vercel's servers worldwide
2. **Free HTTPS**: Secure connection, no extra setup
3. **Fast Loading**: Vercel has servers everywhere, so it loads fast for everyone
4. **Auto-Deploy** (if connected to GitHub): Push code → site updates automatically
5. **Preview Deployments**: Each branch/PR gets its own preview URL

## What's Next?

Suggest next steps:
- "Want to add more features to your site?"
- "Want to connect a custom domain?"
- "Want to learn how to make changes and see them deploy automatically?"

## Quick Reference

For future deployments, they just need:

```bash
# Make changes, then:
git add .
git commit -m "Description of changes"
git push

# That's it! Vercel auto-deploys.

# Or manually deploy:
vercel --prod
```
