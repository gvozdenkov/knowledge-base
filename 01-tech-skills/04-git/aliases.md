# Git Aliases

Add any aliase:

```bash
git config --global alias.ALIAS_NAME "command with spaces"
```

Remove alias:

```bash
git config --global --unset alias.ALIAS_NAME
```

## Pretty Log

Print last 15 commits in colorized graph with time and commiter name:

```bash
git config --global alias.ls "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(brightblack)/ %an%C(reset)%C(auto)%d%C(reset)' -15"
```

Print all commits in the same way:

```bash
git config --global alias.lsa "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(brightblack)/ %an%C(reset)%C(auto)%d%C(reset)' --all"
```

## Commit

```bash
git config --global alias.cm 'commit -m'
```
