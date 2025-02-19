# A Guide to Resolving Merge Conflicts

## Understanding Merge Conflicts
When merging branches in Git, conflicts occur when the same lines of a file are modified in different ways in two branches. Git cannot automatically decide which version to keep and marks the conflicting section with **conflict markers**.

---

## **Example Merge Conflict Layout**
When Git detects a conflict in `README.md`, it inserts markers like this:

```md
# ICS4U Travel Guide 🌍

## Entries
- 🇫🇷 Paris, France  
<<<<<<< HEAD
  - Walk along the Seine River.
- 🇮🇹 Rome, Italy - Explore the Colosseum.
=======
  - Visit the Eiffel Tower!
- 🇯🇵 Tokyo, Japan - Try authentic sushi.
>>>>>>> development
```

---

## **Breaking Down the Merge Conflict Layout**
| Symbol | Meaning |
|---------|------------|
| `<<<<<<< HEAD` | **Start of your current branch's changes (`mr_cheng`)** |
| `=======` | **Separator between conflicting changes** |
| `>>>>>>> development` | **Start of the incoming changes from `development`** |

---

## **How to Resolve a Merge Conflict**

### **1️⃣ Using GitHub Web Interface (No Local Git Required)**
1. Open the **Pull Request (PR) page** where the conflict is detected.
2. Scroll down to the **"This branch has conflicts that must be resolved"** section.
3. Click **"Resolve conflicts"**.
4. The conflicting file will open in an online editor.
5. **Manually edit the file**, choosing which version to keep or combining changes.
6. Click **"Mark as resolved"**.
7. Click **"Commit merge"**.
8. Merge the Pull Request.

✅ Best if you’re working entirely in GitHub without a local Git setup.

---

### **2️⃣ Using VS Code IDE (Graphical Approach)**
1. Open your project in **VS Code**.
2. Pull the latest changes:  
   ```bash
   git pull origin development
   ```
3. If a merge conflict appears, VS Code will highlight the conflicting lines.
4. Click **"Accept Current Change"**, **"Accept Incoming Change"**, or **"Accept Both"**.
5. Manually edit if needed to combine changes.
6. Save the file.
7. Stage and commit the resolved file:
   ```bash
   git add README.md
   git commit -m "Resolved merge conflict in README.md"
   ```
8. Push the fixed branch:
   ```bash
   git push origin mr_cheng
   ```

✅ Best for students using VS Code with Git integration.

---

### **3️⃣ Using Command Line Git (For Terminal Users)**
1. Ensure you're on your branch (e.g., `mr_cheng`):
   ```bash
   git checkout mr_cheng
   ```
2. Merge the `development` branch:
   ```bash
   git merge development
   ```
   If conflicts exist, Git will show:
   ```bash
   CONFLICT (content): Merge conflict in README.md
   Automatic merge failed; fix conflicts and then commit the result.
   ```
3. Open the file in a text editor (VS Code, Nano, Vim, etc.):
   ```bash
   nano README.md  # Or use `vim README.md` or `code README.md`
   ```
4. Locate the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
5. **Edit the file manually** to resolve the conflict.
6. Stage and commit the file:
   ```bash
   git add README.md
   git commit -m "Resolved merge conflict in README.md"
   ```
7. Push the resolved branch:
   ```bash
   git push origin mr_cheng
   ```

✅ Best for students comfortable with command-line Git.

---

## **Summary**
- **`<<<<<<< HEAD`** = Your branch’s version (`mr_cheng`).
- **`=======`** = Separates the two conflicting changes.
- **`>>>>>>> development`** = The incoming changes from `development`.
- You must **manually edit the file** to resolve the conflict before committing.

---

## **Additional Tips**
- If you get stuck during a merge, you can **abort it** with:
  ```bash
  git merge --abort
  ```
- If you prefer a **visual tool**, use VS Code or GitHub Desktop to resolve conflicts.

