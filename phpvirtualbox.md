# Installing phpvirtualbox

```console
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
sudo usermod -a -G disk vbox # for real harddisk virtualization
sudo passwd vbox # remember the password, we'll need it

cat << EOL > path/to/phpvirtualbox/run-server.sh
#!/bin/bash
_dir="$( cd "$( dirname "${BASH_SOURCE[0]}" )" >/dev/null 2>&1 && pwd )"
php -S 0.0.0.0:1234 -t $_dir
EOL


> 1. Edit path/to/phpvirtualbox/config.php accordingly
> 2. Install VirtualBox Extension Pack from https://www.virtualbox.org/wiki/Downloads
>    in order to be able to use "Console". 
```
## Running: 

```
# run in a separate terminal: (workaround for buggy `systemctl start vboxweb-service`)
sudo -u vbox vboxwebsrv --background

path/to/phpvirtualbox/run-server.sh

# Connect to ip-address:1234
```
> Note: Phpvirtualbox's web console  requires Adobe Flash Player Plugin on the client, 
> and isn't working correctly. Use Remmina (or similar) instead.
