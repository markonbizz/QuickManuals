-   [Intro](#intro)
-   [Update System Package Manager](#update-system-package-manager)
-   [Install necessary tools & dependencies](#install-necessary-tools-dependencies)
-   [Install "NVM" (Node Version Manager)](#install-nvm-node-version-manager)
-   [Install "Pyenv"](#install-pyenv)
-   [Install "Poetry"](#install-poetry)
-   [Configuration for "NVM", "Pyenv", and "Poetry"](#configuration-for-nvm-pyenv-and-poetry)
-   [Clone Project Files](#clone-project-files)

# **YapersX Server Enviroment Setup Guide**

## Intro
This manual will guide you through the whole setup without concerns.

## Update System Package Manager
1. **Debian based (Ubuntu / Raspberry Pi OS, etc)** :
	```sh
	apt update && apt upgrade -y
	```
- Additional Notes :
	- Add `sudo` if nessessary

## Install necessary tools & dependencies
1. **Debian based (Ubuntu / Raspberry Pi OS, etc)** :
	```sh
	apt install -y git curl wget build-essential libssl-dev zlib1g-dev \
	libbz2-dev libreadline-dev libsqlite3-dev libncursesw5-dev xz-utils \
	tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
	```
 
- Additional Notes :
	- Add `sudo` if nessessary

## Install "NVM" (Node Version Manager)
1. Download & install latest version : [**"Official Installation Guide"**](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating)
	- You may need to restart your terminal to take effects

2. **Install nodejs through "nvm"** :
	```sh
	nvm install node
	```
	- This will install current latest version

- Additional Notes :
	- For more details, please head to the [**"Official Github"**](https://github.com/nvm-sh/nvm)

## Install "Pyenv"
1. **Execute Official Installer** :
	```sh
	curl https://pyenv.run | bash
	```

2. Install **"Python 3.8"** :
	```sh
	pyenv install 3.8.19
	```

- Additional Notes :
	- For more details, please head to [**"Official Github"**](https://github.com/pyenv/pyenv)

## Install "Poetry"
1. **Automatic Installer** :
	- **Install** : 
		```sh
		curl -sSL https://install.python-poetry.org | python3 -
		```
	- **Uninstall** : 
		```sh
		curl -sSL https://install.python-poetry.org | python3 - --uninstall
		```

 - Additional Notes :
	- For more details, please head to [**"Official Site"**](https://python-poetry.org/docs/#installation)

## Configuration for "NVM", "Pyenv", and "Poetry"
1. Append following lines under **".bashrc", ".zshrc"**, or any **Bourne-compatible shell configuration files**:
	```sh
	# Poetry & Other Local Executable Exports
	export PATH="$HOME/.local/bin:$PATH"

	# Pyenv Exports
	export PYENV_ROOT="$HOME/.pyenv"
	[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
	eval "$(pyenv init -)"
	```
	These lines enable **"nvm", "pyenv"**, and **"poetry"** on your shell

2. After the modification, restart your terminal, check if installation was successfully by executing following lines:
	```sh
	nvm --version
	poetry --version
	pyenv --version
	```
	if thoes runs without errors, then you are good to go.

3. Execute configuration:
	- **"Poetry"**
		```sh
		poetry config virtualenvs.in-project true
		```
	You may need to restart your terminal to take effects

- Additional Notes :
	- For more details, please head to [**"NVM"**](https://github.com/nvm-sh/nvm), [**"Poetry"**](https://python-poetry.org/docs/#installation), [**"Pyenv"**](https://github.com/pyenv/pyenv)

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
