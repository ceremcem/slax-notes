# Installing phpvirtualbox

```
sudo apt-get install virtualbox-5.2
sudo apt-get install php7.0-common php7.0-mysql php7.0-soap php-pear

# /start: Not effective yet
cat << EOL > /etc/default/virtualbox
VBOXWEB_USER=vbox
VBOXWEB_HOST=127.0.0.1
EOL
# /end 

sudo groupadd vboxusers
sudo useradd -d /home/vbox -m -g vboxusers -s /bin/bash vbox
sudo passwd vbox # remember the password, we'll need it

cat << EOL > path/to/phpvirtualbox/run-server.sh
#!/bin/bash
_dir="$( cd "$( dirname "${BASH_SOURCE[0]}" )" >/dev/null 2>&1 && pwd )"
php -S 0.0.0.0:1234 -t $_dir
EOL

# run in a terminal: (workaround for buggy `systemctl start vboxweb-service`)
sudo -u vbox vboxwebsrv --background

> edit path/to/phpvirtualbox/config.php accordingly

path/to/phpvirtualbox/run-server.sh
```
