# git cli

### Append untracked files to .gitignore
- Powershell
    - ```git status --porcelain | Select-String "^\?\?" | ForEach-Object { $_.Line.Substring(3) } | Out-File -FilePath ".gitignore" --Append```
- Bash
    - ```git st --porcelain | grep ?? | cut -c4- >> .gitignore```

### Add changes to previous (not last) commit
```
git add <my fixed files>
git commit --fixup=OLDCOMMIT
git rebase --interactive --autosquash OLDCOMMIT^
```

OLDCOMMIT is the hash for the commit you wish to append to.

### See number of changed lines
- From COMMIT1 to COMMIT2
    - ```git diff --shortstat <COMMIT1> <COMMIT2>```
- From COMMIT1 to HEAD and unstaged
    - ```git diff --shortstat <COMMIT>```
- From COMMIT1 to HEAD ignoring changes unstaged/untracked
    - ```git diff --cached --shortstat <COMMIT>```
    - ```git diff --shortstat <COMMIT> HEAD```



---


---
---

# gh cli
### Query list of .gitignore templates from github using `gh` cli.
- ```gh api gitignore/templates```  

---

### Pull a .gitignore template from github using `gh` cli.
- ```gh api gitignore/templates/{name} --jq ".source" >> .gitignore```  
Be aware, this added NUL between each character for some reason.
I used search/replace to fix it. ```%s/\0//g```

---

### Query list of license templates from github using `gh` cli.
- ```gh api licenses```
- Note: This give the results as JSON. You could filter with jq.

---

