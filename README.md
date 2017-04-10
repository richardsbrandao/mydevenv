# MyDevEnv

## Prerequisite 

### To install virtualbox + vagrant
$ sudo apt-get install virtualbox
$ sudo apt-get install vagrant
$ sudo apt-get install virtualbox-dkms

### To install ansible
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install ansible

## Resources

5 Machines for development.

- Machine ready for java deveplopment
  - Sdkman
  - Java 7
  - Java 8
- Machine ready for ruby deveplopment
  - RVM
  - Ruby 2.3
- Machine ready for nodejs deveplopment
  - Node 6
- Machine ready for elixir deveplopment
  - Elixir 1
- Machine ready for several services
  - Docker
  - Docker-Compose with several services

All machines comes with Docker, Docker-Compose and Git (with some aliases)


## X Server
The java machines comes with a simple XServer, to help you with some IDE.

When you enter in a java machine, you can type **startXServer**
