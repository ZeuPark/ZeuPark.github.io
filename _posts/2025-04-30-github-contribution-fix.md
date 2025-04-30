---
title: "Why GitHub Contributions Don't Show Up and How I Fixed It"
date: 2025-04-30
categories:
  - Git
tags:
  - github
  - git
  - contribution
  - blog
---

Today I encountered an issue where my commits did **not appear in the GitHub contribution graph**, even though everything seemed fine. Here's what happened and how I solved it.

## 🐞 Problem

I committed and pushed to a public repository, but the contribution graph on my GitHub profile didn’t reflect it.

## ✅ Checks I Performed

### 1. Checked Git Config

```bash
git config --list
```

Output:

```bash
user.name=ZeuPark
user.email=parkzeu68@gmail.com
```

✅ Email matched my GitHub account.

---

### 2. Checked Recent Commit Info

```bash
git log -1
```

Output:

```bash
commit 51f9e01...
Author: ZeuPark <parkzeu68@gmail.com>
Date:   Wed Apr 30 09:09:40 2025 +0900

    website python update
```

✅ Author and email were correct.

---

### 3. Still Not Showing in Contributions?

#### Cause:
> GitHub only tracks commits **if the author email matches your GitHub account**.  
> **Past commits** made with an incorrect email **will never appear** in your contribution graph.

---

## 🛠️ Summary Checklist

| Item | Description |
|------|-------------|
| ✅ Email Check | `git config user.email` must match your GitHub account email |
| ✅ Author Check | Use `git log -1` to verify author info |
| ✅ Pushed | If not pushed, it won’t show on GitHub |
| ✅ Public Repo | Only public repos count (unless private contributions are enabled) |
| ✅ Delay | Contributions may take up to 30 minutes to show |

---

## 🔄 What if You Want Past Commits to Count?

You'd need to:

1. Change the commit author via `git rebase` or `git filter-repo`
2. Amend the commits:  
```bash
git commit --amend --author="ZeuPark <parkzeu68@gmail.com>"
```
3. Force push:
```bash
git push --force
```

⚠️ Be careful! This rewrites Git history.

---

Now that the email is correctly set, **future commits will show up as contributions** with no problem.

this post made by chatgpt contribution test