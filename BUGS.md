## git pull issue from remote to local

### Problem
I did a pull request from a branch to `main` on remote. While trying to pull my changes to local, I had this error:
```bash
fatal: bad object refs/remotes/origin/stg_model_bld
error: github.com:Isaac-Tolu/dbt-training.git did not send all necessary objects
```
> **A bit of context**: This is the first time I used `head` to refer to current working branch and also the first time I'm doing a `git pull` without `rebase`
### Solution
- I deleted the `stg_model_bld` branch from local and also deleted it manually from `.git/ refs/remotes/origin/`. `git pull` worked after this
### After-effects
- Refer to this [bug](#git-status-issue)
### References
- [Stack Overflow](https://stackoverflow.com/questions/37145151/how-to-handle-git-gc-fatal-bad-object-refs-remotes-origin-head-error)
- [Github Community](https://github.community/t/github-pulling-issue/248615)

## git status issue

### Problem
This happened after solving this [bug](#git-pull-issue-from-remote-to-local). I created a new branch to work on a new feature, and tried checking status with `git status`. Then I had this error:
```bash
error: bad signature 0x00000000
fatal: index file corrupt
```
### Solution
- I deleted the `.git/index` file and reset git to last commit version
    ```bash
    rm -f .git/index
    git reset
    ```
### References
- [Stack Overflow](https://stackoverflow.com/questions/1115854/how-to-resolve-error-bad-index-fatal-index-file-corrupt-when-using-git)