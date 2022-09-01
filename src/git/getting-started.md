# Getting Started

1. Download Git from: [https://git-scm.com/downloads](https://git-scm.com/downloads)
2. Generate SSH key
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
3. Go into your repository hosting service and create new ssh key
    -   GitHub: [https://github.com/settings/ssh/new](https://github.com/settings/ssh/new)
4. Copy generated public SSH key from `/home/you/.ssh/id_ed25519.pub` to ssh key field
5. Create file `.gitconfig` in `/home/you` directory and paste provided text below with your information
```
[user]
name = your_name
mail = your_email@example.com
email = your_email@example.com
[alias]
find-merge = "!sh -c 'commit=$0 && branch=${1:-HEAD} && (git rev-list $commit..$branch --ancestry-path | cat -n; git rev-list $commit..$branch --first-parent | cat -n) | sort -k2 -s | uniq -f1 -d | sort -n |  tail -1 | cut -f2'"
show-merge = "!sh -c 'merge=$(git find-merge $0 $1) && [ -n \"$merge\" ] && git show $merge'"
```