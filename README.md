# GDG at LSU GitHub Workshop

Welcome! This is where you'll make your very first **pull request**. You'll copy a template, fill in your info, and send it to us to add to this repo. By the end, your name will be part of this workshop's history, and you'll be ready to submit your own project at Geaux Hack.

## Quick vocab

| Term | What it means |
| --- | --- |
| **Repository (repo)** | A project folder that Git tracks, including its full history |
| **Fork** | Your own copy of someone else's repo, on your GitHub account |
| **Clone** | Downloading a repo from GitHub to your computer |
| **Branch** | A separate line of work, so your changes don't touch `main` until they're approved |
| **Commit** | A saved snapshot of your changes, with a message describing them |
| **Push** | Uploading your commits from your computer to GitHub |
| **Pull request (PR)** | Asking the original repo's owners to pull your changes into their project |

## Steps

### 1. Fork this repo

Click **Fork** in the top-right corner of this page, then **Create fork**. You now have your own copy at `github.com/your-github-username/github-workshop`.

### 2. Clone your fork

On **your fork's** page, click the green **Code** button and copy the HTTPS link. Then in your terminal:

```bash
git clone https://github.com/your-github-username/github-workshop.git
cd github-workshop
```

### 3. Create a branch

```bash
git checkout -b add-your-github-username
```

This keeps your work separate from `main`. It's a good habit for every change you make.

### 4. Copy the template and rename it

```bash
cp members/TEMPLATE.md members/your-github-username.md
```

(On Windows Command Prompt, use `copy members\TEMPLATE.md members\your-github-username.md`.)

### 5. Fill in your info

Open `members/your-github-username.md` in any editor (VS Code works great) and replace the placeholder text. The template looks like this:

```markdown
# Your Name

- **GitHub:** [@your-github-username](https://github.com/your-github-username)
- **Major:** Your major
- **Year:** Freshman / Sophomore / Junior / Senior / Grad
- **Fun fact:** Something about you

> One thing I want to build at Geaux Hack: ...
```

Only edit your own file. Don't change `TEMPLATE.md` or anyone else's file.

### 6. Commit your change

```bash
git status
git add members/your-github-username.md
git commit -m "Add your-github-username to the workshop"
```

`git status` shows what changed. `git add` stages your file, and `git commit` saves the snapshot.

First time using Git? Set your name and email first:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### 7. Push to your fork

```bash
git push origin add-your-github-username
```

If it asks you to sign in, use your GitHub account. You may need a personal access token or the GitHub CLI (`gh auth login`) instead of your password.

### 8. Open a pull request

Go to your fork on GitHub. You'll see a yellow banner saying your branch had recent pushes. Click **Compare & pull request**. Then:

- Make sure **base repository** is this repo and **base** is `main`
- Give it a title like `Add your-github-username`
- Click **Create pull request**

That's it, you've opened your first pull request!

## What happens on our end

Once your PR is open, a workshop organizer (a **maintainer** of this repo) takes over:

1. **We review it.** We look at the **Files changed** tab to see exactly which lines you added. GitHub shows this as a *diff*: green lines are added, red lines are removed.
2. **We may ask for changes.** If something's off (wrong folder, edited the template, a typo in your link), we leave a comment on your PR. To fix it, edit your file locally, then `git add`, `git commit` and `git push` again on the same branch. Your PR updates automatically; there's no need to open a new one.
3. **We approve and merge.** Merging copies your commit into this repo's `main` branch. Your file now lives in the official repo, and your commit is in its history for good.
4. **GitHub closes your PR** and marks it as **Merged** in purple. Check the `members/` folder here and you'll see your file.

This review-then-merge flow is how almost every team and open source project works, including the one you'll build at Geaux Hack.

## After it's merged (optional)

Your fork doesn't update by itself. To get everyone else's files too:

- On your fork's page, click **Sync fork**, then **Update branch**.
- Then on your computer:

```bash
git checkout main
git pull origin main
```

You can delete your `add-your-github-username` branch once the PR is merged.

## Stuck?

Raise your hand and an organizer will come help. Common fixes:

- **"Permission denied" when pushing:** you cloned the original repo instead of your fork. Re-clone using your fork's link.
- **Can't find "Compare & pull request":** go to the **Pull requests** tab on your fork and click **New pull request**.
- **Pushed to the wrong branch:** that's OK. Just tell us, and we'll sort it out together.
