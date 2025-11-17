# Git & GitHub — Daily Scenarios

---

<details>
<summary><b>1. Your team reports merge conflicts during a PR — how do you resolve them step-by-step?</b></summary>

### Steps:
<ul>
<li>Start by pulling the latest changes from the target branch (usually <code>main</code> or <code>master</code>).</li>
<li>Checkout your feature branch and rebase or merge the target branch into it.</li>
<li>Identify conflicted files and open them in an editor.</li>
<li>Manually fix conflict markers (<code>&lt;&lt;&lt;&lt;&lt;&lt;&lt;</code>, <code>=======</code>, <code>&gt;&gt;&gt;&gt;&gt;&gt;&gt;</code>).</li>
<li>Mark conflicts as resolved and add the files back to staging.</li>
<li>Complete the merge or rebase operation.</li>
<li>Push the updated branch and continue with the pull request.</li>
</ul>

### Commands used in this scenario:

<pre>
git checkout main
git pull origin main
git checkout feature-branch
git merge main        # or git rebase main
git status
# Fix conflicts manually
git add &lt;conflicted-file&gt;
git merge --continue   # or git rebase --continue
git push origin feature-branch
</pre>

</details>

---

<details>
<summary><b>2. You accidentally pushed secrets/credentials to GitHub — how do you fix it quickly and safely?</b></summary>

### Steps:
<ul>
<li>Immediately rotate or revoke the exposed credential (API key, token, password).</li>
<li>Remove the secret from the file and commit the fix.</li>
<li>Use <code>git filter-repo</code> or BFG to remove the secret from Git history.</li>
<li>Force-push the cleaned repository to overwrite GitHub history.</li>
<li>Enable GitHub secret scanning to avoid future exposures.</li>
<li>Ask team members to re-clone because history changed.</li>
</ul>

### Commands used in this scenario:

<pre>
# Remove secret from file
vim config.yaml
git add config.yaml
git commit -m "Remove exposed secret"

# Clean full history
git filter-repo --replace-text secrets.txt

# Force push
git push origin --force --all

# (Optional) Remove file entirely from history
git filter-repo --path config.yaml --invert-paths
</pre>

</details>

---
