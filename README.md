# My Config

### .bashrc
```bash
#
# ~/.bashrc
#

# If not running interactively, don't do anything
[[ $- != *i* ]] && return

# git prompt and completion
source ~/.completion/git-completion.bash
source /usr/share/git/completion/git-prompt.sh

git_branch() {
  __git_ps1 '[$s]'
}

# Custom bash prompt via kirsle.net/wizards/ps1.html
PS1='\[$(tput bold)\]\[$(tput setaf 3)\][\t]\n\[$(tput setaf 2)\][\[$(tput setaf 2)\]\u\[$(tput setaf 4)\]@\[$(tput setaf 6)\]\h\[$(tput setaf 6)\]\[$(tput setaf 2)\]] \[$(tput setaf 4)\]\w\[$(tput setaf 2)\] $(__git_ps1 "[%s]") \n└─ \$ \[$(tput sgr0)\]'
#PROMPT_COMMAND="\[$(tput bold)\]\[$(tput setaf 3)\][\t]\n\[$(tput setaf 2)\][\[$(tput setaf 2)\]\u\[$(tput setaf 4)\]@\[$(tput setaf 6)\]\h\[$(tput setaf 6)\]\[$(tput setaf 2)\]] \[$(tput setaf 4)\]\w\[$(tput setaf 2)\] $(__git_ps1 "[%s]") \n└─ \$ \[$(tput sgr0)\]"

export GIT_PS1_SHOWDIRTYSTATE=true
export GIT_PS1_SHOWUNTRACKEDFILES=true


# Some alias
alias ls='ls --color=auto'
alias ll='ls -CFlh'
alias la='ls -CFlah'
alias .gt="gnome-terminal $(pwd)"
alias wrkspaces="cd ~/dev/workspaces"
alias fixkeyboard="~/.scripts/fixkeyboard.sh"
alias turnOffScreenSaver="~/.scripts/turnOffScreenSaver.sh"
alias virtualenv="~/.local/bin/virtualenv"
alias aws="~/.local/bin/aws"
alias vivo="cat ~/Documents/vivo.router"

# ADB
alias adb=/home/gomes/dev/ides/android-sdk-linux/platform-tools/adb
alias fastboot=/home/gomes/dev/ides/android-sdk-linux/platform-tools/fastboot
export PATH="/home/gomes/dev/ides/android-sdk-linux/tools:/home/gomes/dev/ides/android-sdk-linux/tools/bin:$PATH"

complete -cf sudo

. /etc/profile.d/vte.sh
###-begin-npm-completion-###
#
# npm command completion script
#
# Installation: npm completion >> ~/.bashrc  (or ~/.zshrc)
# Or, maybe: npm completion > /usr/local/etc/bash_completion.d/npm
#

if type complete &>/dev/null; then
  _npm_completion () {
    local words cword
    if type _get_comp_words_by_ref &>/dev/null; then
      _get_comp_words_by_ref -n = -n @ -w words -i cword
    else
      cword="$COMP_CWORD"
      words=("${COMP_WORDS[@]}")
    fi

    local si="$IFS"
    IFS=$'\n' COMPREPLY=($(COMP_CWORD="$cword" \
                           COMP_LINE="$COMP_LINE" \
                           COMP_POINT="$COMP_POINT" \
                           npm completion -- "${words[@]}" \
                           2>/dev/null)) || return $?
    IFS="$si"
  }
  complete -o default -F _npm_completion npm
elif type compdef &>/dev/null; then
  _npm_completion() {
    local si=$IFS
    compadd -- $(COMP_CWORD=$((CURRENT-1)) \
                 COMP_LINE=$BUFFER \
                 COMP_POINT=0 \
                 npm completion -- "${words[@]}" \
                 2>/dev/null)
    IFS=$si
  }
  compdef _npm_completion npm
elif type compctl &>/dev/null; then
  _npm_completion () {
    local cword line point words si
    read -Ac words
    read -cn cword
    let cword-=1
    read -l line
    read -ln point
    si="$IFS"
    IFS=$'\n' reply=($(COMP_CWORD="$cword" \
                       COMP_LINE="$line" \
                       COMP_POINT="$point" \
                       npm completion -- "${words[@]}" \
                       2>/dev/null)) || return $?
    IFS="$si"
  }
  compctl -K _npm_completion npm
fi
###-end-npm-completion-###

source /opt/bash-wakatime/bash-wakatime.sh

# grep colorize
alias grep=grep --color=auto

export ANDROID_HOME=${HOME}/dev/ides/android-sdk-linux
export PATH=${PATH}:${ANDROID_HOME}/tools
export PATH=${PATH}:${ANDROID_HOME}/platform-tools

export VISUAL="vim" 

export EDITOR="$VISUAL"
export GIT_EDITOR=$VISUAL

export TRANSMISSION_WEB_HOME="/home/gomes/tmp/react-transmission.0.1.0"

export WORKON_HOME="/home/gomes/dev/workspaces/virtual_envs"
source /usr/bin/virtualenvwrapper.sh
```
