
# 📝 Git: Force Pull from Remote (Overwrite Local)

This guide explains how to pull the latest changes from a remote repository and **make your local branch exactly match the remote**, overwriting any local changes if needed.

---

## 🟢 Simple Git Pull Overwrite (Force Update Local)

Run the following commands:

```bash
git fetch origin
git reset --hard origin/main
```

🔹 Replace `main` with your branch name if it’s not `main`.

### ✅ What it does:
- `git fetch origin` → Downloads the latest changes from the remote repository.
- `git reset --hard origin/main` → Resets your local branch to exactly match the remote branch.

⚠️ **Warning**: This will discard **all local changes**, including uncommitted and committed ones.

---

## 🟢 Alternative: Pull with Rebase

If you want to pull the latest changes **but keep your local commits on top**, use:

```bash
git pull --rebase origin main
```

✅ This is **safe** if you only have local commits that you want to keep.

---

## 🟣 Completely Overwrite Everything (Clean Slate)

If your local repository is **broken or completely out of sync** and you want to start fresh:

```bash
git fetch --all
git reset --hard origin/main
git clean -fd
```

- `git clean -fd` → Deletes all untracked files and directories.  
- ✅ This gives you a **completely clean copy** of the remote branch.

---

## 🔥 TL;DR: Force Pull as It Is

For a quick reset:

```bash
git fetch origin
git reset --hard origin/main
```

---

## ⚠️ Notes

- Always make sure you don’t have important local changes before running `reset --hard`.
- Replace `origin` and `main` if your remote or branch names are different.
