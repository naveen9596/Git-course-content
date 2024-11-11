In Git, handling conflicts and performing rollbacks are essential skills for managing collaborative projects, where multiple developers may work on the same files simultaneously. Here’s a guide to effectively handle conflicts and roll back changes in Git.

---

### **1. Handling Conflicts in Git**

Conflicts usually arise when merging branches, rebasing, or pulling changes from a remote repository.

#### **Common Scenarios Causing Conflicts**
   - Two developers modify the same lines of a file.
   - A file is deleted in one branch and modified in another.
   - Different branches modify adjacent lines in the same file, causing a conflict.

#### **Resolving Conflicts**

1. **Identify Conflicts**: Git will notify you of conflicts when they occur, and files with conflicts will have markers.
   - Conflict markers appear within files:
     ```
     <<<<<<< HEAD
     // Your changes
     =======
     // Incoming changes from the other branch
     >>>>>>> branch-name
     ```

2. **Resolve the Conflict**:
   - **Manually** edit the conflicting files by deciding which changes to keep.
   - Remove the conflict markers (`<<<<<<<`, `=======`, and `>>>>>>>`).
   - Save the changes once you’re done.
   - Tools like **VS Code**, **GitKraken**, or **Git’s default mergetool** can help visualize and resolve conflicts interactively.

3. **Stage the Changes**:
   - After resolving conflicts, stage the changes using:
     ```bash
     git add <file>
     ```

4. **Complete the Merge**:
   - Once all conflicts are resolved, complete the merge or rebase:
     ```bash
     git commit -m "Resolved merge conflicts"
     ```
     For a rebase, continue with:
     ```bash
     git rebase --continue
     ```

#### **Using Git Commands to Avoid Conflicts**
   - **git pull --rebase**: Use `git pull --rebase` instead of `git pull` to rebase your changes on top of the remote branch, which minimizes conflicts.
   - **Feature Branches**: Use feature branches and keep them up-to-date with the main branch to avoid large-scale conflicts.

---

### **2. Rollback Options in Git**

Git provides multiple ways to undo changes. The right approach depends on what needs to be undone: staged changes, committed changes, or merging changes.

#### **Common Rollback Commands**

1. **Undo Unstaged Changes**:
   - To discard changes in your working directory:
     ```bash
     git checkout -- <file>
     ```
   - To discard all unstaged changes:
     ```bash
     git checkout -- .
     ```

2. **Undo Staged Changes**:
   - To unstage files without losing the changes:
     ```bash
     git reset <file>
     ```
   - To unstage all files:
     ```bash
     git reset
     ```

3. **Reverting a Commit**:
   - To revert a specific commit without removing it from the history:
     ```bash
     git revert <commit-hash>
     ```
   - This will create a new commit that undoes the changes of the specified commit.

4. **Using git reset to Rollback Commits**:
   - **Soft Reset**: Moves the `HEAD` pointer back but keeps the changes in your working directory and staging area.
     ```bash
     git reset --soft <commit-hash>
     ```
   - **Mixed Reset** (default): Moves the `HEAD` pointer back and keeps changes in the working directory (unstaged).
     ```bash
     git reset --mixed <commit-hash>
     ```
   - **Hard Reset**: Moves `HEAD` and discards all changes. This is **destructive** and should be used cautiously.
     ```bash
     git reset --hard <commit-hash>
     ```

5. **Undoing a Merge**:
   - If a merge commit has already been completed, but needs to be undone:
     ```bash
     git revert -m 1 <merge-commit-hash>
     ```
   - The `-m 1` option tells Git to keep the main branch as the baseline, undoing only the merged branch's changes.

6. **Stash Changes**:
   - If you have uncommitted changes that you need to save temporarily to switch branches or pull updates:
     ```bash
     git stash
     ```
   - To reapply the stashed changes:
     ```bash
     git stash pop
     ```

#### **Best Practices for Rollbacks**
   - **Create Backups**: Before performing a hard reset, create a branch or backup to avoid losing work.
   - **Use `revert` for Shared History**: When collaborating, prefer `git revert` over `reset` to avoid rewriting history.
   - **Stay Updated**: Pull frequently to keep your local branch updated and minimize conflicts.

---

### **Summary Table of Commands**

| Action | Command |
|--------|---------|
| Resolve Conflicts | Manually edit conflicts, `git add <file>`, `git commit` |
| Undo Unstaged Changes | `git checkout -- <file>` |
| Unstage Staged Changes | `git reset <file>` |
| Revert a Commit | `git revert <commit-hash>` |
| Soft Reset (keep all changes) | `git reset --soft <commit-hash>` |
| Mixed Reset (keep unstaged changes) | `git reset --mixed <commit-hash>` |
| Hard Reset (discard all changes) | `git reset --hard <commit-hash>` |
| Undo Merge Commit | `git revert -m 1 <merge-commit-hash>` |
| Stash Changes Temporarily | `git stash`, `git stash pop` |

---

### **Conclusion**

Handling conflicts and rollbacks in Git is crucial for maintaining code integrity in collaborative projects. Understanding these techniques enables efficient workflow management and minimizes disruptions during the development process.
