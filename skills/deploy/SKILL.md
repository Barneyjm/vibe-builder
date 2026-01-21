---
name: deploy
description: Set up automatic deployments so pushing to GitHub deploys to Vercel. Use this to connect GitHub Actions for continuous deployment.
---

# Set Up Automatic Deployments

You are helping someone set up GitHub Actions so that **pushing code = deploying their site**. This is the simplest mental model: commit your changes, push, and your site updates automatically.

## The Goal

After this setup:
- `git push` → Site automatically updates
- No extra commands to remember
- No manual deployment step
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

## Step 2: Link Project to Vercel

This creates the Vercel project and gets the IDs we need:

```bash
vercel link --yes
```

This creates a `.vercel` directory with project settings.

## Step 3: Get Vercel Credentials

We need three things for GitHub Actions:

### Get the Project ID and Org ID

```bash
cat .vercel/project.json
```

Note the `projectId` and `orgId` values.

### Create a Vercel Token

Open the Vercel tokens page:
- macOS: `open https://vercel.com/account/tokens`
- Linux: `xdg-open https://vercel.com/account/tokens`
- Windows: `start https://vercel.com/account/tokens`

Guide them:
1. Click "Create"
2. Name it something like "GitHub Actions"
3. Set scope to the project or full account
4. Copy the token (they won't see it again!)

## Step 4: Add Secrets to GitHub

Add the three secrets to their GitHub repository:

```bash
# Add each secret (they'll be prompted for the value)
gh secret set VERCEL_TOKEN
gh secret set VERCEL_ORG_ID
gh secret set VERCEL_PROJECT_ID
```

For each one, paste the corresponding value when prompted.

**Explain**: "These secrets let GitHub Actions deploy to Vercel on your behalf. They're encrypted and secure."

## Step 5: Create the GitHub Actions Workflow

Create the workflow file:

```bash
mkdir -p .github/workflows
```

Then create `.github/workflows/deploy.yml` with this content:

```yaml
name: Deploy to Vercel

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

env:
  VERCEL_ORG_ID: ${{ secrets.VERCEL_ORG_ID }}
  VERCEL_PROJECT_ID: ${{ secrets.VERCEL_PROJECT_ID }}

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install Vercel CLI
        run: npm install -g vercel

      - name: Pull Vercel Environment
        run: vercel pull --yes --environment=${{ github.event_name == 'push' && 'production' || 'preview' }} --token=${{ secrets.VERCEL_TOKEN }}

      - name: Build Project
        run: vercel build ${{ github.event_name == 'push' && '--prod' || '' }} --token=${{ secrets.VERCEL_TOKEN }}

      - name: Deploy to Vercel
        id: deploy
        run: |
          url=$(vercel deploy --prebuilt ${{ github.event_name == 'push' && '--prod' || '' }} --token=${{ secrets.VERCEL_TOKEN }})
          echo "url=$url" >> $GITHUB_OUTPUT
          echo "Deployed to: $url"
```

## Step 6: Commit and Push

```bash
git add .
git commit -m "Add automatic deployment via GitHub Actions"
git push
```

## Step 7: Watch the Magic

Open GitHub Actions to see it deploy:

```bash
gh run watch
```

Or open in browser:
- macOS: `open $(gh repo view --json url -q .url)/actions`
- Linux: `xdg-open $(gh repo view --json url -q .url)/actions`

**Explain what's happening**:
- "See that running workflow? That's GitHub building and deploying your site"
- "Every time you push, this runs automatically"
- "Green checkmark = your site is updated!"

## Step 8: Celebrate!

Once the action completes, their site is live! Get the URL:

```bash
vercel ls --yes | head -5
```

Open it for them and celebrate:
"Your site is LIVE and will now update automatically every time you push code!"

## The New Workflow

From now on, deploying is just:

```bash
git add .
git commit -m "What you changed"
git push
```

That's it. No `vercel` command needed. Push = Deploy.

**Bonus**: Pull requests automatically get preview URLs, so they can test changes before merging.

## Troubleshooting

**Action failed?**
- Check the workflow logs: `gh run view`
- Usually it's a missing secret or typo

**Site not updating?**
- Make sure they pushed to `main` branch
- Check if the action is running: `gh run list`

**Secret issues?**
- Re-add with `gh secret set VERCEL_TOKEN` etc.
- Make sure the Vercel token hasn't expired
