# GDG at LSU GitHub Workshop

Welcome! This is where you'll make your very first **pull request**. You'll copy a template, fill in your info, and send it to us to add to this repo. By the end, your name will be part of this workshop's history, and you'll be ready to submit your own project at Geaux Hack.

## Quick vocab

| Term | What it means |
| --- | --- |
| **Repository (repo)** | A project folder that Git tracks, including its full history |
| **Fork** | Your own copy of someone else's repo, on your GitHub account |
| **Clone** | Downloading a repo from GitHub to your computer |
| **origin / upstream** | `origin` is your fork (where you push). `upstream` is this GDG repo (where you pull updates from and send your pull request) |
| **Branch** | A separate line of work. Here, `main` is the final project, `dev` is the shared working version, and you make your own branch for your change |
| **Commit** | A saved snapshot of your changes, with a message describing them |
| **Push** | Uploading your commits from your computer to GitHub |
| **Pull request (PR)** | Asking the repo's owners to merge your branch into theirs |

## Before you start

You need Git, a GitHub account, and the GitHub CLI signed in:

```bash
git -v
gh auth login     # pick GitHub.com → HTTPS → Login with a web browser
gh auth status    # should say you're logged in to github.com
```

## Steps

### 1. Fork and clone

```bash
gh repo fork GDSCLSU/Github-Workshop-Fall-2026 --clone
cd Github-Workshop-Fall-2026
```

This makes your own copy (your fork) and downloads it. Your fork is `origin`, and the GDG repo is `upstream`.

<details>
<summary>No GitHub CLI? Do it this way instead</summary>

Click **Fork** at the top of this page, then:

```bash
git clone https://github.com/<your-username>/Github-Workshop-Fall-2026
cd Github-Workshop-Fall-2026
git remote add upstream https://github.com/GDSCLSU/Github-Workshop-Fall-2026.git
```

</details>

### 2. Branch from dev

```bash
git switch dev
git pull upstream dev
git switch -c add-<your-name>
```

Start from the latest `dev`, then make your own branch named after your change, like `add-malik`.

### 3. Copy the template and rename it

```bash
cp members/TEMPLATE.md members/<your-name>.md
```

This works in Mac/Linux terminals, Git Bash and PowerShell. (In Windows Command Prompt, use `copy members\TEMPLATE.md members\<your-name>.md`.)

### 4. Fill in your info

Open your new file and replace the placeholder text:

```bash
notepad members/<your-name>.md   # Windows
nano members/<your-name>.md      # Mac / Linux (Ctrl+O, Enter to save; Ctrl+X to exit)
```

The template looks like this:

```markdown
# Your Name

- **GitHub:** [@your-github-username](https://github.com/your-github-username)
- **Major:** Your major
- **Year:** Freshman / Sophomore / Junior / Senior / Grad
- **Fun fact:** Something about you

> One thing I want to build at Geaux Hack: ...
```

Only edit your own file. Don't change `TEMPLATE.md` or anyone else's file. Then check your work:

```bash
git status
git diff
```

### 5. Stage your change

```bash
git add members/<your-name>.md
git diff --staged
```

Read the diff before committing: only your `.md` file should show up.

### 6. Commit

```bash
git commit -m "Add <your-name> member file"
git log --oneline
```

Write the message as what the commit does. (Want a standard format? See [conventionalcommits.org](https://www.conventionalcommits.org).)

### 7. Push to your fork

```bash
git status
git push -u origin add-<your-name>
```

Never push `.env` files or anything that belongs in `.gitignore`.

### 8. Open a pull request

1. Open your fork on GitHub and click **Compare & pull request**
2. Set **base repository** to `GDSCLSU/Github-Workshop-Fall-2026` and **base** to `dev`
3. Add a title, then click **Create pull request**

**Base must be `dev`, never `main`.**

Have the GitHub CLI? You can do it in one line instead:

```bash
gh pr create --repo GDSCLSU/Github-Workshop-Fall-2026 --base dev --fill
```

That's it, you've opened your first pull request!

## What happens on our end

Once your PR is open, a GDG officer (a **maintainer** of this repo) takes over:

1. **We review it.** We open the **Files changed** tab to see exactly which lines you added. GitHub shows this as a *diff*: green lines are added, red lines are removed.
2. **We may ask for changes.** If something's off (wrong folder, edited the template, base set to `main`), we comment on your PR. To fix it, edit your file, then `git add`, `git commit` and `git push` again on the same branch. Your PR updates automatically; no need to open a new one.
3. **We approve and merge into `dev`.** We click **Review changes → Approve**, then **Merge pull request**. Your commit is now part of the GDG repo's history for good.
4. **GitHub marks your PR as Merged** (purple). Check the `members/` folder on the `dev` branch and you'll see your file.
5. **Later, `dev` gets merged into `main`.** That's how real teams work: changes land in `dev`, get tested together, then go to `main` when they're ready.

## After your PR is merged

Sync your computer with the latest `dev`, which now includes everyone's files:

```bash
git switch dev
git pull upstream dev
```

You can delete your `add-<your-name>` branch once it's merged.

## Stuck?

Raise your hand and an officer will come help. Common fixes:

- **"Permission denied" when pushing:** you cloned the GDG repo instead of your fork. Use `gh repo fork ... --clone`, or re-clone your fork's link.
- **PR shows lots of files or conflicts:** your base is probably `main`. Edit the PR and change the base to `dev`.
- **`git pull upstream dev` fails:** add the remote with `git remote add upstream https://github.com/GDSCLSU/Github-Workshop-Fall-2026.git`.
- **Can't find "Compare & pull request":** go to the **Pull requests** tab on your fork and click **New pull request**.
