# 🚀 How to Publish This Portfolio on GitHub

Follow these steps to create a GitHub account and put this portfolio online.

## Step 1 — Create a GitHub account
1. Go to **https://github.com/signup**
2. Enter your email → create a password → pick a username
   (suggestion: `abdulmuhammad-sec`, `abdulmuhammad-cyber`, or `am-security`).
3. Solve the verification puzzle and confirm the code sent to your email.
4. Choose the **Free** plan.

> ⚠️ Account creation needs your own email + a human verification step, so it must be
> done by you in the browser. It only takes ~2 minutes.

## Step 2 — Install Git (one time)
- Download: **https://git-scm.com/download/win**
- Install with default options.

## Step 3 — Create the repository on GitHub
1. Click the **+** (top-right) → **New repository**.
2. Name it **`cybersecurity-portfolio`**.
3. Set it to **Public** (so recruiters can see it).
4. **Do NOT** add a README/.gitignore (this folder already has them).
5. Click **Create repository**.

## Step 4 — Push this folder to GitHub
Open **PowerShell** in this folder and run (replace `USERNAME`):

```powershell
cd "C:\Users\muham\cybersecurity-portfolio"
git init
git add .
git commit -m "Initial commit: cybersecurity portfolio"
git branch -M main
git remote add origin https://github.com/USERNAME/cybersecurity-portfolio.git
git push -u origin main
```

If prompted to log in, a browser window will open — sign in to authorize.

## Step 5 — (Optional) Make a GitHub Profile README
1. Create a **new repository named exactly your username** (e.g. `abdulmuhammad-sec/abdulmuhammad-sec`).
2. Check "Add a README file".
3. Paste the content from [`PROFILE_README.md`](PROFILE_README.md) into it.
4. This shows up on your GitHub profile homepage.

## Step 6 — Personalize
Search-and-replace these placeholders across the files:
- `YOUR_GITHUB_USERNAME` → your actual username
- `[your professional email]` → your email
- `your-handle` → your LinkedIn handle

Done! Share the repo link on your résumé and LinkedIn. 🎉
