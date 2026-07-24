# 📈 GitHub Contributions Activity Generator

A Python script that generates local git history and commits to backfill your GitHub contributions calendar.

## ⚠ Recommendations & Best Practices

1. **Keep Your Profile Repo Clean**:
   We recommend running this script on a **separate, new public or private dummy repository** (e.g. `github-activity-history`) rather than directly on your profile repository (`HarshSuryawanshi9090/HarshSuryawanshi9090`).
   GitHub aggregates contributions from *all* repositories. A dedicated dummy repository keeps your profile repository's history clean and readable while still populating your contribution chart.

2. **Verify Git Email**:
   Ensure your local git configuration is using the email registered with your GitHub account:
   ```bash
   git config --get user.email
   ```
   If it doesn't match, set it globally:
   ```bash
   git config --global user.email "harshsuryawanshi85@gmail.com"
   ```

---

## 🚀 Execution Instructions

### 1. Create a Target Repository
Go to GitHub and create a new repository (e.g., `github-activity-history`). 
*   **Do not** initialize it with a README, license, or `.gitignore` file. Keep it completely empty.

### 2. Run the Generator Script
Open a terminal (Command Prompt, PowerShell, or Git Bash) in this directory and execute the script.

#### Option A: Default Settings
This creates commits for the past 365 days (committing on roughly 80% of those days, with 1 to 10 commits per day) and automatically pushes the changes to your target repository:
```bash
python contribute.py --repository=https://github.com/HarshSuryawanshi9090/github-activity-history.git
```

#### Option B: Customizable Activity (e.g., Working Days Only)
To customize commits to occur only on weekdays (no weekends) and adjust the commit density:
```bash
python contribute.py --no_weekends --max_commits=6 --frequency=65 --repository=https://github.com/HarshSuryawanshi9090/github-activity-history.git
```

### 3. Parameters Reference
*   `-nw` or `--no_weekends`: Exclude weekend days from commit generations.
*   `-mc` or `--max_commits`: Maximum commits to make per day (Accepts 1 to 20, default is 10).
*   `-fr` or `--frequency`: Percentage probability that a day receives commits (0 to 100, default is 80).
*   `-db` or `--days_before`: Number of days to backfill before the current date (default is 365).
*   `-da` or `--days_after`: Number of days to commit in the future (default is 0).
*   `-r` or `--repository`: Remote git repository URL to automatically link and push the generated commits.
