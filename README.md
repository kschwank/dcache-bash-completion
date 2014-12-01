dcache-bash-completion
======================

A bash completion script for dCache

If dCache is installed this script will allow tab completion for dCache commands
and even tab complete domain names where needed.

To use with bash simply copy the script to /etc/bash_completion.d/dcache

zsh can use bash completion scripts with a little help:

Add the following to your .zshrc:

    _have()
    {
      type $1 &>/dev/null
    }

    have() {
      unset -v have
      _have $1 && have=yes
    }

    bash_source() {
      alias shopt=':'
      alias _expand=_bash_expand
      alias _complete=_bash_comp
      emulate -L sh
      setopt kshglob noshglob braceexpand

      source "$@"
    }

    autoload bashcompinit
    bashcompinit
    bash_source /etc/bash_completion.d/dcache
