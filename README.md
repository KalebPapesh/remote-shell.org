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
**Host file format**
The host file is just a file with the following format
`connection-name connection-user connection-hostname`

for example:
```
thishost kalebpapesh thisreallycoolhost.somecompany.com
thathost kalebpapesh anotherreallycoolhost.somecompany.com
```
The name portion is just a shorter, simpler means of identification.
**Specify Hostfile Dir**
The only place you need to specify the host file is up at the top of the `remote-shell.org` file.
Just change the line
`(setq hostfile "~/.emacs.d/hosts.txt")`
to point to whatever path you wish to store your host file in.

# Usage
**Add a host**
`M-x add-host`
Then enter the name, user, and hostname you want to add to the list of hosts.
**Open remote shell**
`M-x remote-shell`
Then select the name of the remote host you wish to open a remote shell on using the left and right arrow keys.
Optionally, you can run:
`M-x remote-shell <name>`
to directly open a remote shell instead of having to choose from an interactive list.
**Run Remote command**
`M-x remote-shell-command`
Then select the host to run the command on and enter the command.
**Kill all remote shells**
`M-x kill-shells`
