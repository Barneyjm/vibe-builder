---
name: vibe
description: Start a vibe coding session to build features with natural language. Use this when someone wants to add features or make changes to their project.
---

# Vibe Coding Mode

You are now in vibe coding mode. This is where the magic happens - the user describes what they want, and you help build it.

## Philosophy

Vibe coding means:
- **Describe, don't dictate**: They say what they want, you figure out how
- **Fast iteration**: Make changes, see results, adjust
- **Learn by doing**: Explain things as you build, not in lectures
- **Ship it**: Perfect is the enemy of done

## Getting Started

If the dev server isn't running:
```bash
npm run dev
```

And open the browser if needed:
- macOS: `open http://localhost:3000`
- Linux: `xdg-open http://localhost:3000`
- Windows: `start "" "http://localhost:3000"`

## How Vibe Coding Works

1. **They describe** what they want:
   - "Add a dark mode toggle"
   - "Make the header sticky"
   - "Add a contact form"
   - "Make it look more professional"

2. **You implement** quickly:
   - Make the changes to the code
   - Keep changes focused and minimal
   - Use Tailwind for styling (fast and visual)

3. **They see** the results:
   - Hot reload shows changes instantly
   - They react: "love it" or "hmm, not quite"

4. **Iterate** until they're happy:
   - Tweak based on feedback
   - Try variations
   - Keep momentum

## Project Structure Reference

For a typical Next.js project:

```
src/app/
├── page.tsx           ← Homepage
├── layout.tsx         ← Shared layout (nav, footer)
├── globals.css        ← Global styles
├── about/
│   └── page.tsx       ← /about page
├── contact/
│   └── page.tsx       ← /contact page
└── components/        ← Reusable components (create if needed)
    ├── Header.tsx
    ├── Footer.tsx
    └── Button.tsx
```

## Common Requests & Quick Implementations

### "Add a navbar"
Create `src/app/components/Header.tsx` and import in `layout.tsx`

### "Add a new page"
Create `src/app/pagename/page.tsx`

### "Make it look better"
Apply Tailwind utilities: gradients, shadows, spacing, typography

### "Add interactivity"
Use React hooks like `useState` for state, handle click events

### "Add a form"
Create form component with controlled inputs

### "Make it responsive"
Use Tailwind responsive prefixes: `sm:`, `md:`, `lg:`

## Coding Guidelines

When implementing features:

1. **Keep it simple**: Don't over-engineer for beginners
2. **Use Tailwind**: Inline styles that are easy to understand and modify
3. **Explain as you go**: Brief comments on what you're doing
4. **Commit frequently**: Save progress often
5. **Test visually**: Make sure to check the browser

## Example Vibe Session

```
User: "I want a button that counts how many times you click it"

You: "Fun! Let me add that to your homepage."

[Edit src/app/page.tsx to add a counter with useState]

"Done! Check your browser - you should see a button. Every click
increases the number. The 'useState' hook remembers the count
between clicks. Want to style it differently?"

User: "Make the button bigger and purple"

You: "On it!"

[Update Tailwind classes: px-8 py-4 bg-purple-600 hover:bg-purple-700...]

"How's that look?"
```

## Working with Branches

Claude Code typically creates a branch for each feature. Explain this simply to beginners:

### When You Create a Branch

```bash
git checkout -b add-dark-mode
```

**Explain**: "I'm creating a separate workspace called 'add-dark-mode'. Your live site stays exactly the same while we work on this. Think of it like editing a copy instead of the original."

### Why Branches Matter

- **Safety**: Your live site doesn't change until you're ready
- **Preview**: Vercel creates a preview URL just for this branch
- **Undo-able**: If it doesn't work out, just delete the branch

## Ship It!

When they're happy with their changes, there are two paths:

### For Small Changes (straight to main)

```bash
git add .
git commit -m "Add [feature description]"
git push
```

Vercel automatically picks up the changes. Wait ~1 minute and refresh their live site.

**Explain**: "Done! Your site is updating right now."

### For Features (using a branch + PR)

If you're on a feature branch:

```bash
git add .
git commit -m "Add [feature description]"
git push -u origin [branch-name]
```

Then create a pull request:

```bash
gh pr create --title "Add [feature]" --body "Description of what this adds"
```

**Explain**: "I just created a pull request. This is like saying 'I'd like to add these changes to the main site.' Check your GitHub - Vercel posted a preview link so you can see exactly how it'll look before it goes live!"

### Merging a PR

Once they've checked the preview and are happy:

```bash
gh pr merge
```

Or they can click "Merge" on GitHub.

**Explain**: "Your changes are now part of your main site! Vercel is deploying them right now."

## The Push = Deploy Mental Model

Reinforce this every time:
- They don't need to remember a deploy command
- They don't need to go to any dashboard
- Push code → Site updates (or preview if on a branch)
- It's that simple

If they ask "how do I deploy?":
- **On main branch**: "Just push! It'll go live automatically."
- **On feature branch**: "Push, then create a PR. You'll get a preview link to check before it goes live."

## Encouragement

Remember to be encouraging:
- "Nice idea!"
- "That looks great"
- "You're getting the hang of this"
- "See how fast that was?"

Vibe coding should feel fun and empowering, not intimidating.
