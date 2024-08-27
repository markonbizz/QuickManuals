# **YapersX Server Enviroment Setup Guide**
## **Introduction**
This manual will guide you through the whole setup without concerns.

For any issue, contact "cbb111237@nptu.edu.tw", or Teams.

I will do my best to reply.

## **Manual**
1. ### Update Ubuntu
	```bash, zsh
	apt update && apt upgrade -y
	```

2. ### Install **nvm** (Node Version Manager)
	- For more details or latest version, please head to the [**"official github"**](https://github.com/nvm-sh/nvm)

	- **Version v0.40.0**
		- **For "curl"**:
			```bash, zsh
			curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
			```

		- **For "wget"**:
			```bash, zsh
			wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
			```
		
3. ### Install **pyenv**
	- For more details, please head to [**"official github"**](https://github.com/pyenv/pyenv)

	- **Requirements** :
		- **Ubuntu** :
			```bash, zsh
	  		sudo apt update; sudo apt install build-essential libssl-dev zlib1g-dev \
			libbz2-dev libreadline-dev libsqlite3-dev curl git \
			libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
	  		```
	- **Automatic Installer** :
		```bash, zsh
		curl https://pyenv.run | bash
		```
	
4. ### Install **poetry**
	- For more details, please head to [**"official site"**](https://python-poetry.org/docs/#installation)

	- **Automatic Installer** :
		- To **Install** : 
			```bash, zsh
			curl -sSL https://install.python-poetry.org | python3 -
			```
		- To **Uninstall** : 
			```bash, zsh
			curl -sSL https://install.python-poetry.org | python3 - --uninstall
			```

5. ### Add Paths
	Add paths for **nvm**, **pyenv**, and **poetry** under **.bashrc**, **.zshrc**, or other **Bourne-compatible shells**

	- For **".bashrc" & ".zshrc"**, append following lines at the end of the file:
		``` bash
		# Poetry & Other Local Executable Exports
		export PATH="$HOME/.local/bin:$PATH"

		# NVM Exports
		export NVM_DIR="$HOME/.nvm"
		[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
		[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

		# Pyenv Exports
		export PYENV_ROOT="$HOME/.pyenv"
		[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
		eval "$(pyenv init -)"
		```

	- After the modify, exit current terminal then relaunch, check if installation was successfully by run following lines:
		```bash, zsh
		nvm --version
		poetry --version
		pyenv --version
		```
		if thoes runs without errors, then you are good to go.

6. ### Clone The Project
	- For **Bridge**:
		```bash, zsh
		git clone -b bridge https://git.csie2.nptu.edu.tw/yapers/yapersX/yapersx-server.git bridge
		```

	- For **Server**:
		```bash, zsh
		git clone -b server https://git.csie2.nptu.edu.tw/yapers/yapersX/yapersx-server.git server
		```

	Now your current folder will have 2 folders, **"bridge"** and **"server"**
	
	- To initialize bridge, run following lines:
		```bash, zsh
		poetry config virtualenvs.in-project true
		cd ./bridge/src/
		poetry shell
		poetry install
		```

	- To initialize server, run following lines:
		```bash, zsh
		cd ./server/
		nvm install node
		npm install
		```
