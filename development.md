# Development tools

## List

| Name | Platform | Use | Download |
| ---- | -------- | --- | -------- |
| Files | Windows | File explorer (file tagging, git integration, ...) | [Download](https://files.community/) |
| Prefix | Multi | Log HTTP class, check Entity Framework | [Download](https://stackify.com/prefix/) |
| Lunacy | Multi | Figma alternative | [Download](https://lunacy.docs.icons8.com) |
| Fork | Multi | Git client GUI | [Download](https://git-fork.com) |
| RoslynPad | Multi | C# Playground | [Download](https://roslynpad.net/) |

## Git QOL improvements

### Add branch ticket name to commit
```bash
#!/bin/bash
# Get the current branch name
BRANCH_NAME=$(git symbolic-ref --short HEAD)

# Get the JIRA number
JIRA=$(echo $BRANCH_NAME | grep -o -E '[0-9A-Z]+-[0-9]+')

#Check if this a normal commit, or an amend
IS_NORMAL_COMMIT=$(grep -c "$JIRA" $1)

# Prepend the JIRA number to the commit message
if [ -n "$JIRA" ] && [ "$IS_NORMAL_COMMIT" -eq 0 ]; then
  sed -i.bak -e "1s/^/$JIRA: /" $1
fi
```
