---
name: create-app
description: Create a new Next.js application with a modern tech stack. Use this to scaffold a new project with TypeScript, Tailwind CSS, and best practices.
---

# Create a New App

You are helping someone create a new web application. You'll use Next.js with a modern, beginner-friendly stack.

## Step 1: Understand Their Vision

Ask: **"What do you want to build?"**

Get a brief description. Examples they might say:
- "A portfolio website"
- "A todo list app"
- "A landing page for my business"
- "I don't know, just something cool"

If they're unsure, suggest a simple but impressive starter:
- A personal portfolio/link-in-bio page
- A simple interactive app (counter, quiz, etc.)

## Step 2: Choose Location

Ask where they want to create the project. Suggest a good default:

```bash
# Check if common directories exist
ls ~/projects 2>/dev/null || ls ~/code 2>/dev/null || ls ~/dev 2>/dev/null
```

Suggest creating in:
- `~/projects` (create if doesn't exist)
- Or their preferred location

```bash
mkdir -p ~/projects
cd ~/projects
```

## Step 3: Create Next.js App

Generate a project name from their idea (lowercase, hyphenated):
- "My Portfolio" → `my-portfolio`
- "Todo App" → `todo-app`
- "Cool Website" → `cool-website`

Run create-next-app with recommended options:

```bash
npx create-next-app@latest PROJECT_NAME --typescript --tailwind --eslint --app --src-dir --use-npm --no-turbopack
```

**Explain the choices briefly:**
- **TypeScript**: Helps catch errors before they happen
- **Tailwind CSS**: Makes styling super easy with utility classes
- **ESLint**: Keeps your code clean and consistent
- **App Router**: The modern way to build Next.js apps
- **src/ directory**: Keeps your code organized

## Step 4: Navigate and Explore

```bash
cd PROJECT_NAME
```

Give them a quick tour of the project:

```
PROJECT_NAME/
├── src/
│   └── app/
│       ├── page.tsx      ← The homepage (we'll edit this!)
│       ├── layout.tsx    ← The wrapper for all pages
│       └── globals.css   ← Global styles
├── public/               ← Static files (images, etc.)
├── package.json          ← Project info and dependencies
└── tailwind.config.ts    ← Tailwind customization
```

**Keep it simple**: "The main file we'll work with is `src/app/page.tsx` - that's your homepage!"

## Step 5: Start Development Server

```bash
npm run dev
```

Open the browser to see it:
- macOS: `open http://localhost:3000`
- Linux: `xdg-open http://localhost:3000`
- Windows: `start http://localhost:3000`

**Exciting moment**: "Your app is running! You should see the Next.js welcome page."

## Step 6: Make It Theirs

Now modify `src/app/page.tsx` based on their idea. Replace the default content with something personalized.

**Example for a portfolio:**
```tsx
export default function Home() {
  return (
    <main className="min-h-screen bg-gradient-to-b from-gray-900 to-gray-800 text-white">
      <div className="container mx-auto px-4 py-16">
        <h1 className="text-5xl font-bold mb-4">Hi, I'm [Name]</h1>
        <p className="text-xl text-gray-300 mb-8">
          Welcome to my corner of the internet.
        </p>
        {/* More content based on their idea */}
      </div>
    </main>
  );
}
```

**Key principles:**
- Start simple, they can add more later
- Use Tailwind classes (explain briefly what they do)
- Make it look good immediately (dark mode, gradients, spacing)
- Personalize it to their name/idea

## Step 7: Initialize Git

```bash
git init
git add .
git commit -m "Initial commit: Created PROJECT_NAME with Next.js"
```

**Explain**: "Git saves snapshots of your code so you can track changes and undo mistakes."

## Success

They now have:
- A working Next.js application
- Running locally on their machine
- Ready for customization and deployment
- Git tracking their changes

Ask: "Want to keep building, or shall we deploy this to the internet?"
