# machine-setup
Set up JS dev environment for Windows WSL / Linux

//INSTALL GIT
sudo apt install git
git config --global user.name 'USERNAME'
git config --global user.email 'USER@EMAIL.COM'
git config --global credential.helper store


//INSTALL NODE
sudo apt install curl
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
    // restart terminal
nvm install node
//Windows
npm install -g win-node-env


//INSTALL HEROKU
//WARNING WE DO NOT USE HEROKU ANYMORE IT ISN'T FREE
sudo snap install heroku --classic
heroku login


//INSTALL VSCODE
sudo snap install code --classic


//INSTALL POSTGRESQL
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install postgresql-14
sudo service postgresql start
sudo -u postgres createuser --superuser $USER
createdb $USER

sudo gedit /etc/postgresql/14/main/pg_hba.conf
    //change all methods to 'trust'

sudo service postgresql restart

//OPTIONAL INSTALL BEEKEEPER STUDIO
wget --quiet -O - https://deb.beekeeperstudio.io/beekeeper.key | sudo apt-key add -
echo "deb https://deb.beekeeperstudio.io stable main" | sudo tee /etc/apt/sources.list.d/beekeeper-studio-app.list
sudo apt update
sudo apt install beekeeper-studio


//OPTIONAL INSTALL POSTMAN
wget -O - https://gist.githubusercontent.com/SanderTheDragon/1331397932abaa1d6fbbf63baed5f043/raw/postman-deb.sh | sh
