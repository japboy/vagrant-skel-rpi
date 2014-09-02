vagrant-skel-rpi
================

My Raspberry Pi bootstrap virtualizing with Vagrant and provisioning with Ansible.

Requirements
------------

* [Raspberry Pi](http://www.raspberrypi.org/)
* [Raspbian](http://www.raspbian.org/)
* [Vagrant](http://www.vagrantup.com/)
* [Ansible](http://www.ansible.com/)

Installation
------------

### Raspbian image

Create a Raspbian bootable SD card:

```
curl -LO http://downloads.raspberrypi.org/raspbian_latest
unzip ./YYYY-MM-DD-codename-raspbian.zip -d .
dd bs=1m if=./YYYY-MM-DD-codename-raspbian.img of=/dev/diskN
```

* [Raspberry Pi Documentation](http://www.raspberrypi.org/documentation/installation/installing-images/README.md)

### rasp-config

Finish the Raspbian initial configuration with `rasp-config`. Make sure to allow access to the Raspberry Pi through SSH.

* [Raspberry Pi Documentation](http://www.raspberrypi.org/documentation/configuration/raspi-config.md)

### .env

Create `.env` file in this directory and save your server IP address, user name, and password of the Raspberry Pi:

```
SERVER='192.168.1.100'
USERNAME='pi'
PASSWORD='raspberry'
```

### Vagrant plugins

Install Vagrant plugins:

```
vagrant plugin install dotenv vagrant-managed-servers
```

* [bkeepers/dotenv](https://github.com/bkeepers/dotenv)
* [tknerr/vagrant-managed-servers](https://github.com/tknerr/vagrant-managed-servers)

Bootstrap
---------

First of all, copy this repository as your project bootstrap, then follow the instruction below.

Start working on the project:

```
cd /path/to/proj
vagrant up --provider=managed
```

Provision the work environment:

```
vagrant provision
```

Log in to the virtualized SSH environment:

```
vagrant ssh
```

Stop working on the project and unlink it:

```
vagrant destroy
```

References
----------

* [\#20 RaspberryPiを仕事で使うためにAnsibleを使う話 | tech.kayac.com - KAYAC engineers' blog](http://tech.kayac.com/archive/20_raspberrypiansible.html)
* [Ansible - Provisioning - Vagrant Documentation](http://docs.vagrantup.com/v2/provisioning/ansible.html)
* [Using Vagrant and Ansible — Ansible Documentation](http://docs.ansible.com/guide_vagrant.html)
* [Best Practices — Ansible Documentation](http://docs.ansible.com/playbooks_best_practices.html)
* [Insanely complete Ansible playbook, showing off all the options](https://gist.github.com/marktheunissen/2979474)

License
-------

Distributed under [Unlicense](http://unlicense.org/)
