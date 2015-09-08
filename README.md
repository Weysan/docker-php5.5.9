# docker-php5.5.9
package docker-compose pour implémenter un environnement LAMP 5.5.9

## Initiation
Create a docker machine
<pre>docker-machine create --driver virtualbox dev</pre>

Share your un directory with your php files (i.e. : /sites) in your virtualbox dev as "www"

Put that docker-compose package in your directory (into /sites/docker)

connect with SSH to your machine
<pre>docker-machine ssh dev</pre>

Mount the directory :
<pre>
mkdir /var/www
sudo mount -t vboxsf www /var/www
</pre>

Install Docker-compose and persist it:
<pre>
sudo -i
curl -L https://github.com/docker/compose/releases/download/1.4.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
cp /usr/local/bin/docker-compose /var/lib/boot2docker/docker-compose
</pre>

Copy the bootlocal.sh into your boot2docker directory :
<pre>sudo cp docker/bootlocal.sh /var/lib/boot2docker/bootlocal.sh</pre>

Restart your machine :
<pre>
Exit
docker-machine restart dev && docker-machine ssh dev
</pre>

You can now initiate the package :
<pre>
docker-compose up
</pre>

## Create a new vhost
You can modify INI settings with the php.ini file in your /sites/docker/php.ini

To add a new vhost, add a new config file in /sites/docker/sites/name-example.conf

Don't forget to restart your machine after those modifications.
