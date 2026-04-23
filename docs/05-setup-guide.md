# 05 · Setup Guide

Step-by-step instructions to get your computer ready to build the site with Claude Code. Follow these in order. Don't skip ahead.

Total time: about 45 minutes if you've never done this before. Faster if you have.

---

## What we're setting up and why

| Tool | What it does |
|---|---|
| **Node.js** | Runs modern web tools and frameworks. Required for Astro. |
| **Git** | Tracks every change you make. Lets us roll back if anything breaks. |
| **GitHub** | Free cloud backup for your code. Also what Cloudflare uses to auto-deploy your site. |
| **Cloudflare Pages** | Free hosting for your website. Deploys automatically from GitHub. |
| **Claude Code** | The AI assistant that writes and edits your site. |
| **Astro** | The web framework we're building the site with. We'll install this during the build. |

---

## Before you start

You'll need:
- Your computer (Mac, Windows, or Linux — all work)
- An internet connection
- Admin access to install software
- Your Namecheap login (not needed today, but keep it handy for when we connect the domain)

---

## Step 1 · Install Node.js (10 min)

Node.js is the runtime that everything else depends on.

### On Mac or Windows

1. Go to **https://nodejs.org**
2. Download the **LTS** version (the "recommended for most users" one — the big green button)
3. Run the installer
4. Click "Next" through everything — all defaults are fine
5. When it finishes, open your terminal:
   - **Mac:** Press `Cmd + Space`, type "Terminal", press Enter
   - **Windows:** Press the Windows key, type "PowerShell", press Enter
6. Type this command and press Enter:
   ```
   node --version
   ```
7. You should see something like `v22.x.x` or similar. If you see a version number, it worked.

**If it says "command not found":** Close your terminal, open a new one, and try again. Sometimes the installer needs the terminal to restart.

---

## Step 2 · Install Git (5 min)

Git is the version control system. It tracks changes so you can roll anything back.

### On Mac

Git usually comes pre-installed. Check by opening Terminal and running:
```
git --version
```

If you see a version, skip to Step 3. If it says "not installed," macOS will prompt you to install Xcode Command Line Tools — click install and wait. That's it.

### On Windows

1. Go to **https://git-scm.com/download/win**
2. Download and run the installer
3. Click "Next" through everything — defaults are fine
4. Open a new PowerShell window and run:
   ```
   git --version
   ```

You should see a version number.

---

## Step 3 · Configure Git (2 min)

Tell Git who you are. This only happens once per computer.

In your terminal, run these two commands (replace with your info):

```
git config --global user.name "Derek Beitz"
git config --global user.email "derek.beitz@soloex.io"
```

No output means it worked.

---

## Step 4 · Create a GitHub account (5 min)

GitHub is where your site's code will live as backup, and what Cloudflare will use to auto-deploy.

1. Go to **https://github.com**
2. Click **Sign up**
3. Use `derek.beitz@soloex.io` as your email
4. Pick a username (suggestion: `derekbeitz` or `soloex`)
5. Verify your email when GitHub sends the confirmation

**That's it.** No plan needed. The free tier does everything we need.

---

## Step 5 · Connect Git to GitHub (10 min)

This lets your computer push code to your GitHub account.

### Option A · Personal Access Token (easier, recommended)

1. Log into GitHub
2. Click your profile picture (top right) → **Settings**
3. Scroll to **Developer settings** (very bottom of left sidebar)
4. Click **Personal access tokens** → **Tokens (classic)**
5. Click **Generate new token** → **Generate new token (classic)**
6. Give it a name: `Soloex Website Build`
7. Set expiration: 90 days (you can refresh it later)
8. Check the box next to **repo** (this grants access to your repositories)
9. Click **Generate token**
10. **Copy the token immediately** — GitHub only shows it once. Paste it somewhere safe (like a password manager or a text file on your desktop temporarily)

When Git asks for a password later, paste this token instead.

### Option B · SSH key (more setup, but more secure)

Skip this unless you already know what you're doing. Option A is fine for a personal project.

---

## Step 6 · Install Claude Code (5 min)

This is the AI assistant that will actually build the site with you.

1. Open your terminal
2. Run this command:
   ```
   npm install -g @anthropic-ai/claude-code
   ```
3. Wait for it to finish (could take 1–2 minutes)
4. Confirm it installed:
   ```
   claude --version
   ```

You should see a version number.

---

## Step 7 · Log into Claude Code (2 min)

1. In your terminal, run:
   ```
   claude
   ```
2. It will prompt you to log in with your Claude account
3. Follow the prompts — it'll open a browser window and ask you to confirm
4. Once logged in, type `exit` to quit Claude Code for now

You're ready to use Claude Code whenever we're ready to build.

---

## Step 8 · Create a Cloudflare account (5 min)

Cloudflare Pages will host your site for free.

1. Go to **https://dash.cloudflare.com/sign-up**
2. Sign up with `derek.beitz@soloex.io`
3. Verify your email

**You don't need to do anything else right now.** We'll connect Cloudflare to GitHub and your domain during the build session.

---

## Step 9 · Create your project folder (2 min)

This is where your website code will live on your computer.

1. In your terminal, navigate to where you want the folder. For example:

   **Mac:**
   ```
   cd ~/Documents
   ```

   **Windows:**
   ```
   cd ~/Documents
   ```

2. Create the project folder:
   ```
   mkdir soloex-website
   cd soloex-website
   ```

3. You're now inside the empty project folder. That's where we'll build.

---

## Step 10 · Open Claude Code in the project folder (1 min)

While inside `soloex-website` in your terminal, run:
```
claude
```

You'll now be in an interactive Claude Code session, ready to build.

Type `exit` and press Enter to quit when you're done. You can come back anytime by navigating to the folder and running `claude` again.

---

## ✅ Setup complete

You should now have:

- ✅ Node.js installed
- ✅ Git installed and configured
- ✅ GitHub account created
- ✅ GitHub connected to your computer
- ✅ Claude Code installed and logged in
- ✅ Cloudflare account created
- ✅ Project folder created

---

## Quick reference — useful commands

| Command | What it does |
|---|---|
| `cd ~/Documents/soloex-website` | Go to the project folder |
| `claude` | Start Claude Code in the current folder |
| `exit` | Quit Claude Code |
| `git status` | See what files have changed |
| `git log --oneline` | See recent changes |

You don't need to memorize these. Claude Code can run them for you — or remind you — during the build.

---

## What happens in the first build session

Once setup is complete and you have your pre-launch items in progress (at least some client logos and Kristin's headshot), we'll:

1. Create the Astro project inside your `soloex-website` folder
2. Set up the basic site structure (folders for pages, components, assets)
3. Build the homepage first (the priority page you identified)
4. Connect the folder to GitHub
5. Connect GitHub to Cloudflare Pages
6. Get a staging URL (e.g., `soloex-website.pages.dev`) so you can see the site live as we build
7. Connect your `soloex.io` domain to the Cloudflare deployment

Plan on 2–3 hours for the first session. Not all at once — we can break it up.

---

## If something goes wrong

Don't panic. Nothing here is irreversible.

- If an install fails, try it again in a new terminal window
- If a command "isn't found," close and reopen your terminal
- If you're stuck, take a screenshot of the error and we'll work through it together in the next conversation

See `06-next-steps.md` for what happens after setup is complete.
