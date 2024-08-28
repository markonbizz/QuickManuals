# **YapersX Server Enviroment Setup Guide**
## **Intro**
This manual will guide you through the whole setup without concerns.

## **Manual**
1. ### Update System Package Manager
 	- **Debian based (Ubuntu / Raspberry Pi OS, etc)** :
		```bash, zsh
		apt update && apt upgrade -y
		```
	 	- Add `sudo` if nessessary

3. ### Install necessary tools & dependencies
	- **Debian based (Ubuntu / Raspberry Pi OS, etc)** :
		```bash, zsh
		apt install -y git curl wget build-essential libssl-dev zlib1g-dev \
	 	libbz2-dev libreadline-dev libsqlite3-dev libncursesw5-dev xz-utils \
	 	tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
		```
	 	- Add `sudo` if nessessary

2. ### Install "NVM" (Node Version Manager)
   	- Download & install latest version : [**"Official Installation Guide"**](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating)
		- You may need to restart your terminal to take effects

	- **Install nodejs through "nvm"** :
		```bash, zsh
		nvm install node
		```
		- This will install current latest version
       
	- For more details, please head to the [**"Official Github"**](https://github.com/nvm-sh/nvm)

4. ### Install "Pyenv"
	- **Prerequisite** :
		- **For Ubuntu** :
			```bash, zsh
	  		apt update; sudo apt install build-essential libssl-dev zlib1g-dev \
			libbz2-dev libreadline-dev libsqlite3-dev curl git \
			libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
	  		```
   			- Add `sudo` if nessessary
    
	- **Execute Official Installer** :
		```bash, zsh
		curl https://pyenv.run | bash
		```
  
	- Install **"Python 3.8"** :
		```bash, zsh
  		pyenv install 3.8.19
  		```
  
	- For more details, please head to [**"Official Github"**](https://github.com/pyenv/pyenv)
 
5. ### Install "Poetry"
	- **Automatic Installer** :
		- **Install** : 
			```bash, zsh
			curl -sSL https://install.python-poetry.org | python3 -
			```
		- **Uninstall** : 
			```bash, zsh
			curl -sSL https://install.python-poetry.org | python3 - --uninstall
			```
   
	- For more details, please head to [**"Official Site"**](https://python-poetry.org/docs/#installation)

6. ### Configuration for "NVM", "Pyenv", and "Poetry"
	- Append following lines under **".bashrc", ".zshrc"**, or any **Bourne-compatible shell configuration files**:
		``` bash, zsh
		# Poetry & Other Local Executable Exports
		export PATH="$HOME/.local/bin:$PATH"

		# Pyenv Exports
		export PYENV_ROOT="$HOME/.pyenv"
		[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
		eval "$(pyenv init -)"
		```
  		These lines enable **"nvm", "pyenv"**, and **"poetry"** on your shell

	- After the modification, relaunch your terminal, check if installation was successfully by executing following lines:
		```bash, zsh
		nvm --version
		poetry --version
		pyenv --version
		```
		if thoes runs without errors, then you are good to go.

	- Execute configuration:
   	  	- **"Poetry"**
   			```bash, zsh
   	  		poetry config virtualenvs.in-project true
   	  		```
		You may need to restart your terminal to take effects

7. ### Clone Project Files
   	- Execute following lines :
		- **Bridge**:
			```bash, zsh
			git clone -b bridge https://git.csie2.nptu.edu.tw/yapers/yapersX/yapersx-server.git bridge
			```
   			- Add `sudo` if nessessary
	
		- **Server**:
			```bash, zsh
			git clone -b server https://git.csie2.nptu.edu.tw/yapers/yapersX/yapersx-server.git server
			```
   			- Add `sudo` if nessessary

	Now your current folder will have 2 folders, **"bridge"** and **"server"**
	
	- To initialize bridge, run following lines:
		```bash, zsh
		cd ./bridge/src/
		poetry shell
		poetry install
  		poetry env use python3.8
  		python main.py
		```
  		At this point, you should see a **"YX PyBridge"** banner on your terminal and other prompts

	- To initialize server, run following lines:
		```bash, zsh
		cd ./server/
		nvm install node
		npm install
  		npm run dev
		```
