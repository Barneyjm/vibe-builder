# Vibe Builder

A Claude Code plugin that takes you from zero to vibe coding hero using GitHub and Vercel.

## What is this?

Vibe Builder is a beginner-friendly plugin that guides complete newcomers through:

1. Setting up a GitHub account
2. Setting up a Vercel account
3. Creating their first web application
4. Deploying it live to the internet
5. Continuing to build with natural language ("vibe coding")

No prior coding experience required.

## Installation
Run these commands inside Claude Code:

```bash
/plugin marketplace barneyjm/vibe-builder
```

```bash
/plugin install vibe-builder@vibe-builder
```

Restart Claude Code to load the plugin

## Available Skills

### `/vibe-builder:start`
The main journey - takes you through everything from account setup to a deployed website.

**Perfect for:** Complete beginners who want the full guided experience.

### `/vibe-builder:setup-github`
Set up a GitHub account and configure the CLI.

**Perfect for:** Users who only need help with GitHub setup.

### `/vibe-builder:setup-vercel`
Set up a Vercel account and configure the CLI.

**Perfect for:** Users who only need help with Vercel setup.

### `/vibe-builder:create-app`
Create a new Next.js application with TypeScript and Tailwind CSS.

**Perfect for:** Users ready to start a new project.

### `/vibe-builder:deploy`
Connect your GitHub repo to Vercel for automatic deployments.

**Perfect for:** Users who want push = deploy (automatic deployments on git push).

### `/vibe-builder:vibe`
Start a vibe coding session to build features with natural language.

**Perfect for:** Ongoing development after initial setup.

## Push = Deploy

The key philosophy: **pushing code should deploy your site**. No extra commands.

This plugin connects your GitHub repo to Vercel's native integration. Once linked:

```bash
git add .
git commit -m "Add cool feature"
git push
# That's it! Site updates automatically.
```

No secrets to manage. No workflow files. Vercel handles everything.

## Tech Stack

This plugin uses an opinionated but beginner-friendly stack:

- **Next.js** - React framework with great defaults
- **TypeScript** - Catches errors before runtime
- **Tailwind CSS** - Utility-first styling that's easy to learn
- **Vercel** - Fast global hosting with native GitHub integration
- **GitHub** - Code hosting and collaboration

## Example Session

```
You: /vibe-builder:start

Claude: Welcome to vibe coding! I'm going to help you go from zero to
having a live website today. First, do you have a GitHub account?

You: No, I don't have one

Claude: No problem! Let me open the GitHub signup page for you...
[Opens browser to github.com/signup]
Let me know when you've created your account!

You: Done!

Claude: Awesome! Now let's set up Vercel for hosting. Do you have
a Vercel account?

... [continues through the journey] ...

You: I want to add a dark mode toggle

Claude: Fun feature! Let me add that to your site...
[Implements dark mode]
Check your browser - you should see a toggle in the header now!
```

## Philosophy

- **Do, don't lecture** - Learn by building, not reading
- **Fast feedback** - See changes instantly
- **Ship early** - Get something live, then iterate
- **Have fun** - Coding should feel empowering

## Requirements

The plugin will help install these if needed:

- Node.js (v18+)
- npm
- Git
- GitHub CLI (`gh`)
- Vercel CLI (`vercel`)

## License

MIT
