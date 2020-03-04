# remote-shell.org
A elisp package that allows you to save a list of hosts in a text file and easily get a remote shell into them or run remote commands on them

# Setup
Add what's below to your `.*shrc` file
**If BASH**
```
if [[ "$TERM" == "dumb" ]]
then
  PS1='> '
fi
```
**If ZSH**
```
if [[ "$TERM" == "dumb" ]]
then
  unsetopt zle
  unsetopt prompt_cr
  unsetopt prompt_subst
  unsetopt rcs
  unset zle_bracketed_paste

  if whence -w precmd >/dev/null; then
      unfunction precmd
  fi
  if whence -w preexec >/dev/null; then
      unfunction preexec
  fi

  PS1='> '
fi
```
Now, add the following to your init file:
**Add to Emacs init file**
```
(org-babel-load-file "~/path/to/remote-shell.org")
```

# Usage
**Add a host**
`M-x add-host`
**Open remote shell**
`M-x remote-shell`
**Run Remote command**
`M-x remote-shell-command`
**Kill all remote shells**
`M-x kill-shells`
