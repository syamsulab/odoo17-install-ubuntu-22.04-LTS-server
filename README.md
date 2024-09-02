# odoo17-install-ubuntu-22.04-LTS-server

```
sudo apt update && sudo apt upgrade -y
```
#### Secure Server
```
sudo apt-get install openssh-server fail2ban
```
#### Install Packages and libraries
```
sudo apt-get install -y python3-pip
```
Use the methods below to install web dependencies and packages. Verify that every package has been installed correctly and without any problems
```
sudo apt-get install python3-dev libxml2-dev libxslt1-dev zlib1g-dev libsasl2-dev libldap2-dev build-essential libssl-dev libffi-dev libmysqlclient-dev libjpeg-dev libpq-dev libjpeg8-dev liblcms2-dev libblas-dev libatlas-base-dev
```
```
sudo apt-get install -y npm
```
```
sudo ln -s /usr/bin/nodejs /usr/bin/node
```
```
sudo npm install -g less less-plugin-clean-css
```
```
sudo apt-get install -y node-less
```
#### Setup Database Server
```
sudo apt-get install postgresql
```
```
sudo su - postgres
```
```
createuser --createdb --username postgres --no-createrole --no-superuser --pwprompt odoo
```
```
psql
```
```
ALTER USER odoo WITH SUPERUSER;
```
If the user runs the aforementioned command, superuser access rights will be guaranteed. Next, log out of Postgres and PSQL
```
\q
```
```
exit
```
####  Create a system user
```
sudo adduser --system --home=/opt/odoo --group odoo
```
#### Get Odoo17 community from git
```
sudo apt-get install git
```
```
sudo su - odoo -s /bin/bash
```
```
git clone https://www.github.com/odoo/odoo --depth 1 --branch 17.0 --single-branch .
```
```
exit
```
#### install Required Python Packages
first remove inside requirment.txt packages then separate install that packge
gevent.
```
sudo pip3 install -r /opt/odoo/requirements.txt
```
```
sudo pip3 install gevent
```
#### Install Wkhtmltopdf
#### AMD
```
sudo wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.bionic_amd64.deb
```
```
sudo dpkg -i wkhtmltox_0.12.5-1.bionic_amd64.deb
```
```
sudo apt install -f
```
#### Ampere
```
sudo wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6.1-2/wkhtmltox_0.12.6.1-2.jammy_arm64.deb
```
```
sudo dpkg -i wkhtmltox_0.12.6.1-2.jammy_arm64.deb
```
```
sudo apt install -f -y
```
#### Setup Conf file
```
sudo nano /etc/odoo.conf
```
```
[options]
; This is the password that allows database operations:
admin_passwd = *Liba1985#
db_host = localhost
db_port = 5432
db_user = odoo
db_password = *Liba1985#
addons_path = /opt/odoo/addons,/opt/custom-addons
logfile = /var/log/odoo/odoo.log
```
```
sudo chown odoo: /etc/odoo.conf
```
```
sudo chmod 640 /etc/odoo.conf
```
```
sudo mkdir /var/log/odoo
```
```
sudo chown odoo:root /var/log/odoo
```
#### Odoo service file
```
sudo nano /etc/systemd/system/odoo.service
```
```
[Unit]
   Description=Odoo17
   Documentation=http://www.odoo.com
   [Service]
   # Ubuntu/Debian convention:
   Type=simple
   User=odoo
   ExecStart=/opt/odoo/odoo-bin -c /etc/odoo.conf
   [Install]
   WantedBy=default.target
```
```
sudo chmod 755 /etc/systemd/system/odoo.service
```
```
sudo chown root: /etc/systemd/system/odoo.service
```
#### Run Odoo17
```
sudo systemctl start odoo.service
```
```
sudo systemctl status odoo.service
```
```
sudo systemctl enable odoo.service
```
#### install nginx
```
apt-get install nginx -y
```
```
ufw allow ssh
ufw allow 80
ufw allow 443
ufw allow 8069
ufw allow 8072
```
```
ufw enable
```
#### set timezone
```
timedatectl set-timezone Asia/....
```
#### Python extra packages
```
pip3 install html2text
```
```
pip3 install phonenumbers
```
```
pip3 install numpy
```
```
pip3 install watchdog
```
```
pip3 install dropbox
```
```
pip3 install pydrive
```
```
pip3 install pyfcm
```
