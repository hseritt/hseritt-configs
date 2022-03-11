# Configs

## Summary

A collection of my favorite configs.

* bashrc: append to ~/.bashrc
* sudoers: copy to /etc/sudoers
* misc: a collection of configs that may not fit in any particular file


## Notes

### bashrc

#### Prompt

Keeps the current path above your prompt and shows the current branch of your git project:

```
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}

PS1="[\[\033[32m\]\w]\[\033[0m\]\n\[\033[1;36m\]\u\[\033[1;33m\]\$(parse_git_branch)=> \[\033[0m\]"
```


Will make your prompt look like:

```
[~/Development/Configs]
devuser(main)=>
```

#### Pyenv and virtualenv

Generally needed for pyenv to work and use virtualenv.

```
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"    # if `pyenv` is not already on PATH
eval "$(pyenv init --path)"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

#### Node version manager

For nvm (install different node versions)

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

#### SDKMan

For SDK Man (manages different JDK and Java packages)

```
export SDKMAN_DIR="$HOME/.sdkman"
[[ -s "$HOME/.sdkman/bin/sdkman-init.sh" ]] && source "$HOME/.sdkman/bin/sdkman-init.sh"
```

### sudoers

Allows your sudo user to run commands as root without password.

```
# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) NOPASSWD: ALL
```



