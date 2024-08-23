# Docker Quick Initialization (Ubuntu Image)
## 1. Setup
Either your OS is `Windows` , `MacOS` , or `Linux-Based Distro`
- [Docker Official](https://www.docker.com/products/docker-desktop/)
```powershell, sh, bash, zsh
docker pull ubuntu:latest
docker run -dit -p 3000:3000 -p 8022:22 --name="(PUT NAME RIGHT HERE)" --privileged --cpus="2" --memory="4G" ubuntu /bin/bash
```


## 2. Execute Container
```powershell, sh, bash, zsh
docker exec -it (CONTAINER'S NAME) /bin/bash
```


## 3. Install Packages
```sh, bash, zsh
apt update && apt upgrade -y && \
apt install -y zsh git curl wget neovim && \
apt install -y build-essential python3 python-is-python3 python3-poetry nodejs npm && \
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
keep pressing `ENTER` until you see a cyan "~" prompt on terminal
---
** Zsh Plugins **
| Plugin | Command |
| :----- | :------ |
| zsh-syntax-highlighting | `git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting` |
| zsh-autosuggestions | `git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions` |


## 4. Modify .zshrc
```sh, bash, zsh
nvim ~/.zshrc
```
- Change / Add Following Lines
```
export EDITOR="nvim"
ZSH_THEME="clean"
alias zshconfig="$EDITOR ~/.zshrc"
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
```
