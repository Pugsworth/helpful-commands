# git cli

### Append untracked files to .gitignore
- Powershell
    - ```git status --porcelain | Select-String "^\?\?" | ForEach-Object { $_.Line.Substring(3) } | Out-File -FilePath ".gitignore" --Append```
- Bash
    - ```git st --porcelain | grep ?? | cut -c4- >> .gitignore```
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

