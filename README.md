Environment-setup
=================

VM with nginx-mysql-php55-mailcatcher

----
## Things you will need

1. [Vagrant](http://www.vagrantup.com/download-archive/v1.5.4.html) installed - 1.5.4 is the version I use as 1.6+ seems to have errors
2. [VirtualBox](https://www.virtualbox.org) installed
3. [Sequel Pro](http://www.sequelpro.com)

# Starting the VM

    git clone git@github.com:innesm4/Environment-setup.git

    cd Environment-setup

    vagrant up 

# Create a virtual host on your machine
    sudo nano /private/etc/hosts

Add
192.168.56.101  boilerplate.dev

# Connect to Sequel pro

1. Create a new SSH connection
2. MySQL host: 192.168.56.101
3. Username: root
4. Password: secret
5. SSH Host: 192.168.56.101
6. SSH Username: vagrant
7: SSH Password: Click the key and select the file- /puphpet/files/dot/ssh/id_rsa 

# Finally

1. Go to boilerplate.dev in your browser and you *should* see the message "This is php"


# Changing the setup
Changes are made in the config.yaml file

1.Change the port (line 10)

    private_network: 192.168.56.101

2.Change the servername (line 104 and 106)

    servername: boilerplate.dev
    serveraliases:
        - www.boilerplate.dev

3. Folder location (line 107)
    www_root: /var/www/boilerplate/web

**This is the location on the VM**

On line 32 of config.yaml note:
    synced_folder:
       pgrRRMmpEv9F:
            source: ./
            target: /var/www

**The root of this repo where the boilerplate folder is the source and is then mapped to /var/www on the VM**

## Deploy this setup to a real server

1. Visit [Puphpet](https://puphpet.com/)
2. Drag the config.yaml into the page
3. Choose Digital Ocean, Rackspace or Amazon
3. Enter your API details
----
## Changelog
* 7-June-2014 initial commit