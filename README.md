# Vagrant + Puppet base

## To mirror this repository please do the following:

    git clone --bare https://github.com/hangarlabs/base-laravel4-admin.git
    # Make a bare clone of the repository

    cd base-laravel4-admin.git
    git push --mirror https://github.com/hangarcr/new-repository.git
    # Mirror-push to the new repository

    cd ..
    rm -rf base-laravel4-admin.git
    # Remove our temporary local repository

This is the base configuration of the project, using Vagrant + Puppet.

## Requirements:
* Have installed ruby [RVM](http://rvm.io/)

* Download and Install the latest version of [VirtualBox](https://www.virtualbox.org/wiki/Downloads). If you have Virtual Box already installed, please make sure you update the version to at least 4.3.6

* Download their Extension Pack [at the same link](https://www.virtualbox.org/wiki/Downloads).

* Download and Install latest version [Vagrant](http://www.vagrantup.com/downloads.html). If you already have an older version o vagrant please uninstall it using "gem uninstall vagrant" before attempting to install the new one.

## Set Up

To install Vagrant Hostmaster just open __Terminal__ application and type:

    vagrant plugin install vagrant-hostsupdater

Clone the entire project.

    git clone https://github.com/hangarcr/base-laravel4-admin.git

Locate the file called __Vagrantfile__ and make sure that you are at the same level.

Start vagrant:

    vagrant up

Everytime you do a __vagrant up__ your computer password could be requested in order to modify your __/etc/hosts__ file.

After *vagrant up* you can access on the browser the following url: http://dev.drupalsinglesite.com/

## Notes

You can edit the IP value, just open __Vagrantfile__ and edit the following line:

    config.vm.network :private_network, ip: "192.168.101.140"

If you want to restore an existing database dump, just place the .sql file on __/vagrant-data/modules/mysql/files/__ with the name __backup.sql__.

This __backup.sql__ will be commited and pushed to the repository everytime is neccesary, so if you do a pull of an updated version of this file, you can update database just running:

    vagrant provision

If you want to connect to the database in the VM server, use the following data:

    host:       192.168.101.140
    user:       root
    password:   root
    database:   db_laravel4admin

You can connect SSH to the VM server using:

    vagrant ssh

To shutdown the VM server just type:

    vagrant halt

You can get rid of the VM server using the command:

    vagrant destroy

