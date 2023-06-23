- 👋 Hi, I’m @Raghava-Ch
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...


# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# Alias definitions
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# Enable programmable completion features
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi

# Append to PATH
export PATH="$HOME/bin:$PATH"

# User-specific environment variables
export LANGUAGE=en_US.UTF-8
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8

# Set the default editor
export EDITOR=vim

# Default prompt configuration
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi

# Append the git branch to the prompt if applicable
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
PS1="$PS1\$(parse_git_branch)"

# Enable color support in the terminal
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)"
    alias ls='ls --color=auto'
    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# Enable history timestamps
export HISTTIMEFORMAT="%F %T "

# Enable history expansion with space
shopt -s histappend
HISTCONTROL=ignoreboth

# Enable case-insensitive tab completion
bind "set completion-ignore-case on"

# Enable autocorrect for 'cd' command
shopt -s cdspell

# Increase command history size
HISTSIZE=10000
HISTFILESIZE=20000

# Display last command's exit status in the prompt
PROMPT_COMMAND='RET=$?; echo -ne "\033[1;37m[\033[0m\033[1;${RET}m$RET\033[0m\033[1;37m]\033[0m"'

# Disable Ctrl+S and Ctrl+Q flow control
stty -ixon

# Fix Ctrl+Backspace behavior in Ubuntu
if [ "$TERM" == "xterm" ]; then
    bind '"\e[9;3~": backward-kill-word'
fi

# Source global configurations if available
if [ -f /etc/bash.bashrc ]; then
    . /etc/bash.bashrc
fi



Raghava-Ch/Raghava-Ch is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
