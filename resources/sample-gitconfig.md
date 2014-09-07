[user]
	name = Your Name
	email = Your Email 
[push]
	default = simple

# settings from rupl
# https://github.com/rupl/dotfiles/blob/master/.gitconfig

[color]
  ui = auto
[color "branch"]
  current = yellow reverse
  local = yellow
  remote = green
[color "diff"]
  meta = yellow bold
  frag = magenta bold
  old = red bold
  new = green bold
[color "status"]
  added = green
  changed = yellow
  untracked = red

[alias]
  st = status
  cm = commit
  br = branch
  co = checkout
  df = diff
  dc = diff --cached
  ds = diff --staged
  dn = diff --numstat
  dns = diff --staged --numstat
  lg = log -p
  lol = log --graph --decorate --pretty=oneline --abbrev-commit
  lola = log --graph --decorate --pretty=oneline --abbrev-commit --all
  lolp = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
  ls = ls-files
  rhh = reset --hard HEAD

  # Show files ignored by git:
  ign = clean -dXn

  # Oneline, but with author and date
  log-date = log --pretty=format:'%C(yellow)%h %Cred%ad %Cblue%an%Cgreen%d %Creset%s' --date=short
  
[help]
	autocorrect = 1
[difftool "Kaleidoscope"]
	cmd = ksdiff --partial-changeset --relative-path \"$MERGED\" -- \"$LOCAL\" \"$REMOTE\"
[mergetool "Kaleidoscope"]
	cmd = ksdiff --merge --output \"$MERGED\" --base \"$BASE\" -- \"$LOCAL\" --snapshot \"$REMOTE\" --snapshot
	trustExitCode = true
[diff]
	tool = Kaleidoscope
[difftool]
	prompt = false
[mergetool]
	prompt = false
[merge]
	tool = Kaleidoscope
[core]
	editor = /usr/bin/vim
[credential]
	helper = osxkeychain
