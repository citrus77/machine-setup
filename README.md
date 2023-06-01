## machine-setup
Set up JS dev environment for Windows WSL / Linux

### INSTALL GIT
```
sudo apt install git
```
```
git config --global user.name 'USERNAME'
git config --global user.email 'USER@EMAIL.COM'
git config --global credential.helper store
```

### GENERATE SSH KEY FOR GITHUB
```
ssh-keygen -t ed25519 -C "your_email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
```
##### copy key and paste in GitHub SSH Key settings


### INSTALL NODE
```
sudo apt install curl
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
```
##### restart terminal
```
nvm install node
```

#### FOR NODE FOR WINDOWS, NOT NEEDED FOR WSL
```
npm install -g win-node-env
```
### INSTALL VSCODE (LINUX ONLY -- NOT FOR WSL)
```
sudo snap install code --classic
```

### INSTALL POSTGRESQL
```
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install postgresql
sudo service postgresql start
sudo -u postgres createuser --superuser $USER
createdb $USER
sudo apt install gedit
sudo gedit /etc/postgresql/15/main/pg_hba.conf
```
#### Postgres for Windows
...
psql -U postgres -c "CREATE ROLE <WINDOWS_USERNAME> LOGIN NOSUPERUSER INHERIT CREATEDB CREATEROLE;"
createdb <WINDOWS_USERNAME>
...

##### change all methods to 'trust' in pg_hba.conf
##### currently the latest version of Postgres is 15 -- change the version number in the path to pg_hba.conf if different
```
sudo service postgresql restart
```
#### OPTIONAL INSTALL BEEKEEPER STUDIO -- LINUX ONLY, NOT FOR WSL (BUT CAN GET WINDOWS INSTALLER FROM GITHUB LINK BELOW)
##### licensing changes, get community edition at [https://github.com/beekeeper-studio/beekeeper-studio](https://github.com/beekeeper-studio/beekeeper-studio)
```
wget --quiet -O - https://deb.beekeeperstudio.io/beekeeper.key | sudo apt-key add -
echo "deb https://deb.beekeeperstudio.io stable main" | sudo tee /etc/apt/sources.list.d/beekeeper-studio-app.list
sudo apt update
sudo apt install beekeeper-studio
```
#### OPTIONAL INSTALL POSTMAN -- LINUX ONLY, NOT FOR WSL
```
wget -O - https://gist.githubusercontent.com/SanderTheDragon/1331397932abaa1d6fbbf63baed5f043/raw/postman-deb.sh | sh
```
