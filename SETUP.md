# How to Publish This Portfolio on GitHub

Follow these steps to put this portfolio online.

## Step 1: Install Git (one time)

- Download from https://git-scm.com/download/win
- Install with the default options.

## Step 2: Create the repository on GitHub

1. Sign in to GitHub and click the plus icon in the top right, then choose New repository.
2. Name it cybersecurity-portfolio.
3. Set it to Public so recruiters can view it.
4. Do not add a README or .gitignore, since this folder already has them.
5. Click Create repository.

## Step 3: Push this folder to GitHub

Open PowerShell in this folder and run the following, replacing USERNAME with your GitHub username:

```powershell
cd "C:\Users\muham\cybersecurity-portfolio"
git remote add origin https://github.com/USERNAME/cybersecurity-portfolio.git
git branch -M main
git push -u origin main
```

If prompted to sign in, a browser window will open. Sign in to authorize the push.

## Step 4: Create a GitHub Profile README (optional)

1. Create a new repository named exactly the same as your username.
2. Check the option to add a README file.
3. Paste the content from PROFILE_README.md into it.
4. This content appears on your GitHub profile homepage.

## Step 5: Personalize

If you later add a LinkedIn profile, add the link to README.md and PROFILE_README.md.

After that, share the repository link on your resume and with employers.
