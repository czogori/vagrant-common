sudo apt-get update

sudo apt-get install -y \
git mc zsh \
postgresql postgresql-contrib

# postgres
sudo -u postgres psql -c "alter user postgres password 'postgres';"
sudo -u postgres psql -c "CREATE ROLE aj WITH LOGIN PASSWORD 'aj' CREATEDB CREATEROLE;"
sudo -u postgres psql -c "create database aj with owner aj;"

# apache
sudo sed -i "s/#listen_addresses = 'localhost'/listen_addresses = '*'/" /etc/postgresql/9.3/main/postgresql.conf
sudo sed -i "s/peer/md5/" /etc/postgresql/9.3/main/pg_hba.conf
sudo sed -i "s/127.0.0.1\/32/0.0.0.0\/0/" /etc/postgresql/9.3/main/pg_hba.conf
sudo /etc/init.d/postgresql restart

# oh my zsh
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
sudo chsh -s $(which zsh) vagrant
wget https://raw.githubusercontent.com/czogori/dotfiles/master/.zshrc -O ~/.zshrc
