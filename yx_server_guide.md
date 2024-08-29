# **YapersX Server Enviroment Setup Guide**

## Table of Contents
- [Intro](#intro)
- [Update System Package Manager](#update-system-package-manager)
- [Install Necessary Tools & Dependencies](#install-necessary-tools--dependencies)
- [Install "NVM" (Node Version Manager)](#install-nvm-node-version-manager)
- [Install "Pyenv"](#install-pyenv)
- [Install "Poetry"](#install-poetry)
- [Clone Project Files](#clone-project-files)


## Intro
This manual will guide you through the whole setup without concerns.


## Update System Package Manager
1. **Debian based (Ubuntu / Raspberry Pi OS, etc)** :
	```sh
	sudo apt update && sudo apt upgrade -y
	```
 
- Additional Notes :
	- Remove `sudo` if nessessary


## Install Necessary Tools & Dependencies
1. **Debian based (Ubuntu / Raspberry Pi OS, etc)** :
	```sh
	sudo apt install -y git curl wget build-essential libssl-dev zlib1g-dev \
	libbz2-dev libreadline-dev libsqlite3-dev libncursesw5-dev xz-utils \
	tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev python3
	```
 
- Additional Notes :
  	- If appears **region selection menu**, please choose `5. Asia`, then `72. Taipei`
	- Remove `sudo` if nessessary


## Install "NVM" (Node Version Manager)
1. Download & install latest version : [**"Official Installation Guide"**](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating)
	- By **"curl"**:
		```sh
	 	curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
	 	```
  
	- By **"wget"**:
		```sh
		wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
	 	```
  
- **Restart your terminal** to take effects

2. Check **nvm version**:
	- By executing following lines to insure **"nvm"** was installed correctly:
 		```sh
   		nvm --version
   		```
 
3. **Install nodejs through "nvm"** :
	```sh
	nvm install node
 	node --version
	```
 
	- This will install current latest version

- Additional Notes :
	- Latest download link on **2024 August, 26**
	- For more details, please head to the [**"Official Github"**](https://github.com/nvm-sh/nvm)


## Install "Pyenv"
1. **Execute Official Installer** :
	```sh
	curl https://pyenv.run | bash
	```
 
2. Export **pyenv path** to your **.bashrc, .zshrc**, or any **Bourne-compatible shell configuration files**
	```sh
 	# Pyenv Exports
	export PYENV_ROOT="$HOME/.pyenv"
	[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
	eval "$(pyenv init -)"
 	```
 
- **Restart your terminal** to take effects

3. Check **pyenv version**:
	- By executing following lines to insure **"pyenv"** was installed correctly:
 		```sh
   		pyenv --version
   		```

4. Install **"Python 3.8"** :
	```sh
	pyenv install 3.8.19
	```

- Additional Notes :
	- For more details, please head to [**"Official Github"**](https://github.com/pyenv/pyenv)


## Install "Poetry"
1. **Download latest version from official site** :
	- **Install** : 
		```sh
		curl -sSL https://install.python-poetry.org | python3 -
		```
  
	- **Uninstall** : 
		```sh
		curl -sSL https://install.python-poetry.org | python3 - --uninstall
		```
  
2. Export **poetry path** to your **.bashrc, .zshrc**, or any **Bourne-compatible shell configuration files**
	```sh
 	# Poetry & Other Local Executable Exports
	export PATH="$HOME/.local/bin:$PATH"
 	```
 
- **Restart your terminal** to take effects
 
3. Check **poetry version**:
	- By executing following lines to insure **poetry** was installed correctly:
 		```sh
   		poetry --version
   		```

- Additional Notes :
	- For more details, please head to [**"Official Site"**](https://python-poetry.org/docs/#installation)


## Clone Project Files
- Execute following lines :
	- **Bridge**:
		```sh
		git clone -b bridge https://git.csie2.nptu.edu.tw/yapers/yapersX/yapersx-server.git bridge
		```
		- Add `sudo` if nessessary

	- **Server**:
		```sh
		git clone -b server https://git.csie2.nptu.edu.tw/yapers/yapersX/yapersx-server.git server
		```
		- Add `sudo` if nessessary

Now your current folder will have 2 folders, **"bridge"** and **"server"**

- To initialize bridge, run following lines:
	```sh
	cd ./bridge/src/
	poetry shell
	poetry install
	poetry env use python3.8
	python main.py
	```
	At this point, you should see a **"YX PyBridge"** banner on your terminal and other prompts

- To initialize server, run following lines:
	```sh
	cd ./server/
	npm install
	npm run dev
	```
 	Now you may go to `http://localhost:3000` to see if server is up
