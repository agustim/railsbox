[![Build Status](https://travis-ci.org/andreychernih/railsbox.svg?branch=master)](https://travis-ci.org/andreychernih/railsbox)
[![Code Climate](https://codeclimate.com/github/andreychernih/railsbox/badges/gpa.svg)](https://codeclimate.com/github/andreychernih/railsbox)
[![Test Coverage](https://codeclimate.com/github/andreychernih/railsbox/badges/coverage.svg)](https://codeclimate.com/github/andreychernih/railsbox)

[railsbox][] is Ruby on Rails virtual machine configurator. You can quickly create virtual machine for development and production environments using this tool. Mac OS X, Linux and Windows host machines are supported.

# Requirements

You will need [VirtualBox][], [vagrant][] and [ansible][] to bootstrap new machine using configuration created by this utility. [ansible][] is not required for Windows, railsbox will use shell scripts to install and run ansible inside guest machine.

# What's included

## Operating systems

You can choose between Ubuntu 12.04 LTS and Ubuntu 14.04 LTS. Base boxes provided by [vagrantcloud][]. You can also deploy to your remote server using SSH connection. [railsbox][] will create 2 scripts:

* `provision.sh` - which will install and configure all required software
* `deploy.sh` - which will deploy latest code from the GIT repo

## Ruby versions

It's possible to install Ruby either with [rvm][], [rbenv][] or using [brightbox apt repository][].

## Application server

Supported servers are:

* [nginx][] and [unicorn][]
* [nginx][] and [puma][] (added by @RDrop)
* [nginx][] and [passenger][]

## Databases

It's possible to install the following databases:

* PostgreSQL
* MySQL
* MongoDB
* redis

## Background jobs

* sidekiq
* resque
* delayed_job

## vim

[vim-sensible][] and [vim-rails][] are automatically installed.

# Future plans

[railsbox][] is constantly improving. The following is in our TODO list for future releases:

* Add ability to deploy to various platforms supported by vagrant - Parallels, VMWare, EC2
* Add additional server options (Passenger, thin)
* Add memcached
* Add elasticsearch
* Add MariaDB
* Add CouchDB
* Add SMTP server

# Contributing

All kind of contributions are always welcomed.

# License

[railsbox][] is licensed under the [MIT license].

[railsbox]: http://railsbox.io/
[vagrant]: https://www.vagrantup.com/
[VirtualBox]: https://www.virtualbox.org/
[ansible]: http://www.ansible.com/
[rvm]: https://rvm.io/
[brightbox apt repository]: https://www.brightbox.com/docs/ruby/ubuntu/
[nginx]: http://nginx.org/
[puma]: http://puma.io/
[unicorn]: http://unicorn.bogomips.org/
[passenger]: https://www.phusionpassenger.com/
[homebrew]: http://brew.sh/
[brew cask]: https://github.com/caskroom/homebrew-cask
[vagrantcloud]: http://vagrantcloud.com
[rbenv]: https://github.com/sstephenson/rbenv
[vim-sensible]: https://github.com/tpope/vim-sensible
[vim-rails]: https://github.com/tpope/vim-rails
[MIT license]: LICENSE


# Setup Debian system.

## [VirtualBox on Debian](https://wiki.debian.org/VirtualBox):
* Active "contrib" component in ``/etc/apt/sources.list`
```
# Debian 8 "Jessie"
deb http://http.debian.net/debian/ jessie main contrib
```
* Update
```
apt-get update
```
* Install
```
apt-get install linux-headers-$(uname -r|sed 's,[^-]*-[^-]*-,,') virtualbox
```

## [Vagrant from debian's repositories](https://packages.debian.org/jessie/vagrant)
* Install
```
apt-get install vagrant
```

[Vagrant](http://www.vagrantup.com/downloads)
* Download .DEB of 32bits or 64bits.
* Install
```
dpkg -i vagrant-\*.deb
```
## [Ansible on debian]()

```
$ sudo apt-get update
$ sudo apt-get install python-pip python-dev git -y
$ sudo pip install PyYAML jinja2 paramiko
$ git clone https://github.com/ansible/ansible.git
$ cd ansible
$ git pull --rebase
$ git submodule update --init --recursive
$ sudo make install

```
