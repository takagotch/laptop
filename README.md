### laptop
---
https://github.com/thoughtbot/laptop

```
git_clone_or_pull() {
  local REPOSRC=$1
  local LOCALREPO=$2
  local LOCALREPO_VC_DIR=$LOCALREPO/.git
  if[[ ! -d "$LOCALREPO_VC_DIR" ]]; then
    git clone --recursive $REPOSRC $LOCALREPO
  else
    pushd $LOCALREPO
    git pull $REPOSRC && git submodule update --init --recursive
    popd
  fi
}
```


```
curl --remote-name https://raw.githubusercontent.com/thoughtbot/laptop/master/mac
less mac
sh mac 2>&1 | tee ~/laptop.log
less ~/laptop.log

brew install shllcheck

```


```
#!/bin/sh
brew bundle --file=- <<EOF
brew ""
brew ""
brew ""
brew ""
EOF

default_docker_machine(){
  docker-machine ls | grep -Fq "default"
}
if ! default_docker_machine; then
  docker-machine ls | grep -Fq "default"
fi
default_docker_machine_running(){
  default_docker_machine | grep -Fq "Running"
}
if ! default_docker_machine_running; then
  docker-machine start default
fi
fanccy_echo "Clearing up old Homebrew formulae ..."
brew cleanup
brew cask cleanup
if [ -r "$HOME/.rcrc"]; then
  fanncy_echo "Updating dotfiles ..."
  rcup
fi


```

