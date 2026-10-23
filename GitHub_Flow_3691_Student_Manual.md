# GitHub Flow – SCM Basics (Project 3691)
# Student Manual — Every Step, In Order

Project: <https://intranet.hbtn.io/projects/3691>

Each step is one action. Do them in order. Do not skip.

🌐 = do it in the browser  ⌨️ = type it in the terminal

Everywhere you see `YOUR-USERNAME`, put your own GitHub username instead.

**Three things that will cost you points if you ignore them:**
1. Run the checker at the end of every task. Never do two tasks and check once.
2. Copy the text exactly. One wrong letter = 0 points.
3. Task 4 must be green before you start Task 6.

**How to run the checker:** open the project on the intranet, scroll to the task,
find the **My GitHub** box, set **Repository** to `holbertonschool-github-flow`,
leave **Folder** empty, click **Run the correction**.

---

# TASK 0 — Fork and Clone
**3 points · you tick this one yourself**

**Step 1.** 🌐 Open <https://github.com> and log in.

**Step 2.** 🌐 Go to <https://github.com/hbtn-edu/github-collab-base>

**Step 3.** 🌐 Click the **Fork** button at the top right.

**Step 4.** 🌐 A form opens. Find the box **Repository name**. Erase `github-collab-base` and type:

```
holbertonschool-github-flow
```

**Step 5.** 🌐 Click **Create fork**.

**Step 6.** 🌐 You are now on your own copy: `https://github.com/YOUR-USERNAME/holbertonschool-github-flow`

**Step 7.** ⌨️ Open your terminal and type:

```bash
mkdir -p ~/scm-github-collab
```

**Step 8.** ⌨️ Type:

```bash
cd ~/scm-github-collab
```

**Step 9.** ⌨️ Type (with your username):

```bash
git clone https://github.com/YOUR-USERNAME/holbertonschool-github-flow.git
```

**Step 10.** ⌨️ Type:

```bash
cd holbertonschool-github-flow
```

**Step 11.** ⌨️ Type:

```bash
git remote add upstream https://github.com/hbtn-edu/github-collab-base
```

**Step 12.** ⌨️ Type:

```bash
git remote -v
```

✓ You must see 4 lines: two for `origin` (your copy) and two for `upstream` (the original).

**Step 13.** ⌨️ Type:

```bash
git status
```

✓ It must say **nothing to commit, working tree clean**. Do not change any file in this task.

**Step 14.** 🌐 Go to the intranet, open Task 0, and tick the self-validation boxes.

---

# TASK 1 — Creating Workspace Branches
**10 points · robot checks this**

**Step 1.** ⌨️ Make sure you are in the project folder:

```bash
cd ~/scm-github-collab/holbertonschool-github-flow
```

**Step 2.** ⌨️ Type:

```bash
git switch main
```

**Step 3.** ⌨️ Type:

```bash
git fetch origin
```

**Step 4.** ⌨️ Type:

```bash
git fetch upstream
```

**Step 5.** ⌨️ Type:

```bash
git merge upstream/main
```

**Step 6.** ⌨️ Type:

```bash
git push origin main
```

**Step 7.** ⌨️ Create the first branch:

```bash
git switch -c feature/intro-update main
```

**Step 8.** ⌨️ Send it to GitHub:

```bash
git push -u origin feature/intro-update
```

**Step 9.** ⌨️ Go back to main:

```bash
git switch main
```

**Step 10.** ⌨️ Create the second branch:

```bash
git switch -c feature/history-update main
```

**Step 11.** ⌨️ Send it to GitHub:

```bash
git push -u origin feature/history-update
```

**Step 12.** ⌨️ Go back to main:

```bash
git switch main
```

**Step 13.** ⌨️ Check your work:

```bash
git ls-remote --heads origin
```

✓ You must see these three lines:

```
refs/heads/main
refs/heads/feature/intro-update
refs/heads/feature/history-update
```

**Step 14.** 🌐 Intranet → Task 1 → **Run the correction**.

🛑 You must see **10/10** before you start Task 2.

---

# TASK 2 — Independent Document Editing
**18 points · robot checks this**

**Step 1.** ⌨️ Switch to the first branch:

```bash
git switch feature/intro-update
```

**Step 2.** ⌨️ Add the sentence to the file. Copy this whole line, do not retype it:

```bash
printf '\n\nThis introduction has been updated as part of collaborative work.\n' >> docs/introduction.md
```

**Step 3.** ⌨️ Check it landed correctly:

```bash
tail -n 1 docs/introduction.md
```

✓ It must print this, and only this:

```
This introduction has been updated as part of collaborative work.
```

✗ If it printed a long sentence about "new contributors", stop and go to Fix A at the end of this manual.

**Step 4.** ⌨️ Type:

```bash
git add docs/introduction.md
```

**Step 5.** ⌨️ Type:

```bash
git commit -m "Update introduction document"
```

**Step 6.** ⌨️ Type:

```bash
git push origin feature/intro-update
```

**Step 7.** ⌨️ Switch to the second branch:

```bash
git switch feature/history-update
```

**Step 8.** ⌨️ Add the other sentence (note it says **history section**, not history document):

```bash
printf '\n\nThis history section has been updated as part of collaborative work.\n' >> docs/history.md
```

**Step 9.** ⌨️ Check it:

```bash
tail -n 1 docs/history.md
```

✓ It must print this, and only this:

```
This history section has been updated as part of collaborative work.
```

**Step 10.** ⌨️ Type:

```bash
git add docs/history.md
```

**Step 11.** ⌨️ Type:

```bash
git commit -m "Update history document"
```

**Step 12.** ⌨️ Type:

```bash
git push origin feature/history-update
```

**Step 13.** ⌨️ Go back to main:

```bash
git switch main
```

**Step 14.** 🌐 Intranet → Task 2 → **Run the correction**.

🛑 You must see **18/18** before you start Task 3.

---

# TASK 3 — Pull Requests and Reviews
**3 points · you tick this one yourself**

**Step 1.** 🌐 Go to `https://github.com/YOUR-USERNAME/holbertonschool-github-flow`

**Step 2.** 🌐 Click the **Pull requests** tab.

**Step 3.** 🌐 Click the green **New pull request** button.

**Step 4.** 🌐 Set the two dropdown menus:
* **base:** `main`
* **compare:** `feature/intro-update`

Both must be your own repository. If the left one says `hbtn-edu`, click **compare across forks** and change it to your username.

**Step 5.** 🌐 Click **Create pull request**.

**Step 6.** 🌐 In the **Title** box, erase everything and type:

```
Update introduction document
```

**Step 7.** 🌐 In the description box, write one full sentence. You can use this:

```
This pull request updates the introduction document as part of collaborative work.
```

**Step 8.** 🌐 Click **Create pull request**.

🛑 Do **not** merge it. You merge in Task 4.

**Step 9.** 🌐 Scroll to the comment box at the bottom of the page and write a sentence about the file. You can use this:

```
The new closing line in docs/introduction.md makes the purpose of the repository clearer for new contributors, so this change improves the completeness of the document.
```

**Step 10.** 🌐 Click **Comment**.

**Step 11.** 🌐 Click the **Pull requests** tab again.

**Step 12.** 🌐 Click **New pull request**.

**Step 13.** 🌐 Set the dropdowns:
* **base:** `main`
* **compare:** `feature/history-update`

**Step 14.** 🌐 Click **Create pull request**.

**Step 15.** 🌐 In the **Title** box type:

```
Update history document
```

**Step 16.** 🌐 In the description box write one full sentence. You can use this:

```
This pull request updates the history section as part of collaborative work.
```

**Step 17.** 🌐 Click **Create pull request**. Do not merge it.

**Step 18.** 🌐 Scroll to the comment box and write a sentence about this file. You can use this:

```
The added line in docs/history.md records how the project evolved, which makes the history easier to follow for anyone reading the documentation later.
```

**Step 19.** 🌐 Click **Comment**.

**Step 20.** 🌐 Intranet → Task 3 → tick the self-validation boxes.

---

# TASK 4 — Merging and Tagging v1.0.0
**10 points · robot checks this**

**Step 1.** 🌐 Open the intranet and look at your scores.

🛑 Task 1 must show **10/10** and Task 2 must show **18/18**. If they do not, go back and finish them now. After Step 5 of this task those 28 points become impossible to get.

**Step 2.** 🌐 Go to your repo → **Pull requests** tab → open **Update introduction document**.

**Step 3.** 🌐 Click **Merge pull request**.

🛑 Use the plain **Merge pull request** button. Do not pick *Squash and merge* or *Rebase and merge*.

**Step 4.** 🌐 Click **Confirm merge**.

**Step 5.** 🌐 Click the grey **Delete branch** button that appears.

**Step 6.** 🌐 Go back to **Pull requests** → open **Update history document**.

**Step 7.** 🌐 Click **Merge pull request**.

**Step 8.** 🌐 Click **Confirm merge**.

**Step 9.** 🌐 Click **Delete branch**.

**Step 10.** ⌨️ Type:

```bash
git switch main
```

**Step 11.** ⌨️ Type:

```bash
git pull origin main
```

**Step 12.** ⌨️ Check both sentences arrived:

```bash
tail -n 1 docs/introduction.md
tail -n 1 docs/history.md
```

✓ Each must print its sentence alone.

**Step 13.** 🌐 Go to your repo's front page. In the right-hand column, click **Releases**.

**Step 14.** 🌐 Click **Draft a new release**.

**Step 15.** 🌐 Click **Choose a tag**, type `v1.0.0`, then click the line **+ Create new tag: v1.0.0 on publish**.

**Step 16.** 🌐 Check that **Target** says `main`.

**Step 17.** 🌐 In **Release title** type exactly:

```
Initial collaborative update
```

**Step 18.** 🌐 In the description write at least two full sentences. You can use this:

```
This release merges the updated introduction document into the main branch. It also includes the updated history section contributed on a separate branch.
```

**Step 19.** 🌐 Click **Publish release**.

**Step 20.** ⌨️ Type:

```bash
git fetch origin --tags --prune
```

**Step 21.** ⌨️ Type:

```bash
git rev-parse origin/main
```

**Step 22.** ⌨️ Type:

```bash
git ls-remote --tags origin v1.0.0
```

✓ The long code from Step 21 must match the long code at the start of Step 22's line.
✗ If they are different, go to Fix B at the end of this manual.

**Step 23.** 🌐 Intranet → Task 4 → **Run the correction**.

🛑 You must see **10/10** before you start Task 6. (Task 5 is safe to do either way.)

---

# TASK 5 — Create a Conflict and Resolve It
**10 points · robot checks this**

**Step 1.** ⌨️ Type:

```bash
git switch main
```

**Step 2.** ⌨️ Type:

```bash
git pull origin main
```

**Step 3.** ⌨️ Create the first branch:

```bash
git switch -c feature/conflict-a main
```

**Step 4.** ⌨️ Type:

```bash
git push -u origin feature/conflict-a
```

**Step 5.** ⌨️ Type:

```bash
git switch main
```

**Step 6.** ⌨️ Create the second branch:

```bash
git switch -c feature/conflict-b main
```

**Step 7.** ⌨️ Type:

```bash
git push -u origin feature/conflict-b
```

**Step 8.** ⌨️ Switch to branch A:

```bash
git switch feature/conflict-a
```

**Step 9.** ⌨️ Replace line 3 of the file. Copy this whole line:

```bash
sed -i '3s/.*/Collaboration requires clear communication and well-defined responsibilities./' docs/collaboration.md
```

**Step 10.** ⌨️ Check it:

```bash
sed -n '3p' docs/collaboration.md
```

✓ Must print:

```
Collaboration requires clear communication and well-defined responsibilities.
```

**Step 11.** ⌨️ Type:

```bash
git commit -am "Update first paragraph for conflict scenario A"
```

**Step 12.** ⌨️ Type:

```bash
git push origin feature/conflict-a
```

**Step 13.** ⌨️ Switch to branch B:

```bash
git switch feature/conflict-b
```

**Step 14.** ⌨️ Replace the same line with different text:

```bash
sed -i '3s/.*/Effective teamwork depends on continuous feedback and shared understanding./' docs/collaboration.md
```

**Step 15.** ⌨️ Check it:

```bash
sed -n '3p' docs/collaboration.md
```

✓ Must print:

```
Effective teamwork depends on continuous feedback and shared understanding.
```

**Step 16.** ⌨️ Type:

```bash
git commit -am "Update first paragraph for conflict scenario B"
```

**Step 17.** ⌨️ Type:

```bash
git push origin feature/conflict-b
```

**Step 18.** 🌐 Go to your repo → **Pull requests** → **New pull request**.

**Step 19.** 🌐 Set **base:** `main` and **compare:** `feature/conflict-a`, then click **Create pull request** twice.

**Step 20.** 🌐 Click **Merge pull request** → **Confirm merge** → **Delete branch**.

**Step 21.** 🌐 Click **Pull requests** → **New pull request**.

**Step 22.** 🌐 Set **base:** `main` and **compare:** `feature/conflict-b`, then click **Create pull request** twice.

**Step 23.** 🌐 GitHub shows a warning: *This branch has conflicts that must be resolved.*

🛑 Do **not** click **Resolve conflicts** on the website. You must fix it in the terminal. Leave this page open.

**Step 24.** ⌨️ Type:

```bash
git switch feature/conflict-b
```

**Step 25.** ⌨️ Type:

```bash
git pull origin main
```

Git stops and says `CONFLICT (content): Merge conflict in docs/collaboration.md`. That is supposed to happen.

**Step 26.** ⌨️ Look at the mess Git left for you:

```bash
sed -n '1,12p' docs/collaboration.md
```

You will see `<<<<<<<`, `=======` and `>>>>>>>` markers with both versions between them.

**Step 27.** ⌨️ Replace the whole file with the agreed version. Copy this **entire block**, all 9 lines, and paste it in one go:

```bash
cat > docs/collaboration.md <<'EOF'
# Collaboration Guidelines

Collaboration requires adaptability, trust, and continuous alignment among team members.

When multiple people work on these documents, it is common for changes to overlap. Overlapping changes can lead to merge conflicts, which are a normal part of a collaborative workflow.

The most important aspect of collaboration is communication. Comments in pull requests, documentation updates, and clear descriptions of changes all help maintain a shared understanding of the project.
EOF
```

**Step 28.** ⌨️ Check no markers are left:

```bash
grep -n '<<<<<<<\|=======\|>>>>>>>' docs/collaboration.md
```

✓ This must print **nothing at all**.

**Step 29.** ⌨️ Check line 3:

```bash
sed -n '3p' docs/collaboration.md
```

✓ Must print:

```
Collaboration requires adaptability, trust, and continuous alignment among team members.
```

**Step 30.** ⌨️ Type:

```bash
git add docs/collaboration.md
```

**Step 31.** ⌨️ Type:

```bash
git commit -m "Resolve conflict in collaboration document"
```

**Step 32.** ⌨️ Type:

```bash
git push origin feature/conflict-b
```

**Step 33.** 🌐 Go back to the pull request page and refresh it. The conflict warning is gone.

**Step 34.** 🌐 Click **Merge pull request** → **Confirm merge** → **Delete branch**.

**Step 35.** ⌨️ Type:

```bash
git switch main
git pull origin main
```

**Step 36.** 🌐 Intranet → Task 5 → **Run the correction**.

🛑 You must see **10/10** before you start Task 6.

---

# TASK 6 — Changelog and Final Release
**10 points · robot checks this**

**Step 1.** 🌐 Open the intranet and check that Task 4 shows **10/10**.

🛑 If it does not, stop and fix Task 4 first. This task moves `main` forward and Task 4 can never pass again afterwards.

**Step 2.** ⌨️ Type:

```bash
git switch main
```

**Step 3.** ⌨️ Type:

```bash
git fetch origin
```

**Step 4.** ⌨️ Type:

```bash
git pull origin main
```

**Step 5.** ⌨️ Create the changelog. Copy this **entire block** and paste it in one go:

```bash
cat > CHANGELOG.md <<'EOF'
## Unreleased
- Updated the introduction and history documents with new content describing the collaborative work done on separate branches.
- Resolved the merge conflict in docs/collaboration.md by agreeing on a single shared paragraph about adaptability and trust.
EOF
```

**Step 6.** ⌨️ Type:

```bash
git add CHANGELOG.md
```

**Step 7.** ⌨️ Type (this message must be exact):

```bash
git commit -m "Update changelog with latest changes"
```

**Step 8.** ⌨️ Type:

```bash
git push origin main
```

**Step 9.** The next version number is **v1.1.0**. (You added new content and broke nothing, so under Semantic Versioning you raise the middle number: 1.0.0 → 1.1.0.)

**Step 10.** ⌨️ Change the heading to the real version:

```bash
sed -i '1s/.*/## v1.1.0/' CHANGELOG.md
```

**Step 11.** ⌨️ Check it:

```bash
head -3 CHANGELOG.md
```

✓ Line 1 must be `## v1.1.0`, followed by your two lines starting with `-`.

**Step 12.** ⌨️ Type:

```bash
git commit -am "Set changelog version to v1.1.0"
```

**Step 13.** ⌨️ Type:

```bash
git push origin main
```

**Step 14.** 🌐 Go to your repo → **Releases** → **Draft a new release**.

**Step 15.** 🌐 Click **Choose a tag**, type `v1.1.0`, then click **+ Create new tag: v1.1.0 on publish**.

**Step 16.** 🌐 Check that **Target** says `main`.

**Step 17.** 🌐 In **Release title** type exactly this (there is **no `v`** in the title):

```
Collaborative update 1.1.0
```

**Step 18.** 🌐 In the description write at least two full sentences. You can use this:

```
This release documents the updates made to the introduction and history documents during the collaborative workshop. It also records the resolution of the merge conflict in docs/collaboration.md, where both contributors agreed on a single shared paragraph.
```

**Step 19.** 🌐 Click **Publish release**.

**Step 20.** ⌨️ Type:

```bash
git fetch origin --tags --prune
```

**Step 21.** ⌨️ Type:

```bash
git rev-parse origin/main
```

**Step 22.** ⌨️ Type:

```bash
git ls-remote --tags origin v1.1.0
```

✓ The two long codes must match.

**Step 23.** 🌐 Intranet → Task 6 → **Run the correction**.

✅ **10/10. You have finished the project.**

---

# Progress sheet

Tick a box only when the intranet shows the points.

```
[ ]  Task 0   Fork and Clone                      3 pts   (tick it yourself)
[ ]  Task 1   Workspace Branches                 10 pts
[ ]  Task 2   Document Editing                   18 pts
[ ]  Task 3   Pull Requests and Reviews           3 pts   (tick it yourself)
[ ]  Task 4   Merging and Tagging v1.0.0         10 pts
[ ]  Task 5   Conflict Resolution                10 pts
[ ]  Task 6   Changelog and Final Release        10 pts
                                          TOTAL  64 pts
```

---

# Fixes

## Fix A — my sentence got glued to the paragraph

⌨️ Run these three lines:

```bash
sed -i '$ s/This introduction has been updated as part of collaborative work\.$//' docs/introduction.md
printf '\n\nThis introduction has been updated as part of collaborative work.\n' >> docs/introduction.md
tail -n 1 docs/introduction.md
```

✓ The last command must print only the sentence. Then commit and push again.

For `docs/history.md`, use the same three lines with the history sentence.

## Fix B — my tag is on the wrong commit

⌨️ Run these lines:

```bash
git fetch origin --tags --prune
git switch main
git pull origin main
git tag -d v1.0.0
git push origin :refs/tags/v1.0.0
git tag v1.0.0
git push origin v1.0.0
```

🛑 Use `git tag v1.0.0`. Never `git tag -a v1.0.0`. The `-a` version makes the robot read two codes instead of one and you fail.

## Fix C — I deleted the branches before Task 1 and 2 were green

⌨️ Find the two commits:

```bash
git fetch origin
git switch main
git pull origin main
git log --oneline --all | grep "Update introduction document"
git log --oneline --all | grep "Update history document"
```

Each line starts with a short code. Use them here:

```bash
git branch feature/intro-update   PASTE-FIRST-CODE-HERE
git branch feature/history-update PASTE-SECOND-CODE-HERE
git push origin feature/intro-update
git push origin feature/history-update
```

Run the checkers for Task 1 and Task 2, collect the points, then delete the branches again:

```bash
git push origin --delete feature/intro-update
git push origin --delete feature/history-update
```

Then run the Task 4 checker again.

## Fix D — the intranet says "git clone failure"

Check these four things in order:

1. 🌐 <https://intranet.hbtn.io/users/me> — is your GitHub username there and spelled right?
2. 🌐 In the **My GitHub** box on the task, is **Repository** set to `holbertonschool-github-flow`?
3. 🌐 Is **Folder (optional)** completely empty?
4. 🌐 Is your fork public? Repo → **Settings** → scroll to the bottom.

## Fix E — lots of red checks at once

Look only at the **top** red one. Some checks switch off everything below them when they fail. Fix the first one and the rest usually go green by themselves.
