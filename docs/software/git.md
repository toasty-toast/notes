# Git

## Tags

```bash
# Create a tag
$ git tag tag1
$ git tag tag2

# List tags
$ git tag
tag1
tag2

# Push tags
$ git push --tags

# Delete local tag
$ git tag -d tag1

# Delete remote tag
$ git push origin :tag1
```

## Useful Aliases

```ini
# In ~/.gitconfig
[alias]
branch-name = "!git rev-parse --abbrev-ref HEAD"
publish = "!git push -u origin $(git branch-name)"
unpublish = "!git push origin :$(git branch-name)"
unstage = "reset HEAD"
```
