# Install Log for web dev related tools/enviornment

## VS Code
> url = https://code.visualstudio.com/docs/setup/linux
1. install key and repo

`$ sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc`

`$ sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'`

2. update package cache and install using dnf

`$ dnf check-update`
`$ sudo dnf install code`

> finished

## Git
> url = https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
1. installs basic git tools via a binary installer

`$ sudo dnf install git-all`

> finsihed git install

## Node (via NVM)
> url = https://github.com/creationix/nvm

1. install script via curl

`$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash`

2. verify installation

> troubleshooting: close and open terminal and try again

`$ command -v nvm`

3. Download and install lastest version of Node

`$ nvm install node`

4. confirm by checking versions of node and npm, each command should return the version

`$ node -v`
`$ npm -v`

## (OPTIONAL) RPM fusion for nonfree repo access

> url = https://rpmfusion.org/Configuration#Installing_Free_and_Nonfree_Repositories

1. `$ sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm`


## Yarn package manager

> install wget - needed for yarn install. You might not have wget depending on distro

`$ sudo dnf install wget`

> url = https://yarnpkg.com/lang/en/docs/install/


1. RPM package repo 

`$ sudo wget https://dl.yarnpkg.com/rpm/yarn.repo -O /etc/yum.repos.d/yarn.repo`

2. intstall view dnf

`$ sudo dnf install yarn`

3. confirm by typing `$ yarn -v` which should print the version of yarn

> finished install of yarn







