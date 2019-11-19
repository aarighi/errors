# Initialize machine on AWS w/ ubuntu

Sort of

    $ sudo apt update -y
    $ sudo apt upgrade
    $ sudo apt autoremove
    $ sudo apt autoclean
    $ sudo apt update -y
    $ sudo apt upgrade
    $ # sudo apt install vim htop nmap -y
    $ vim my_ssh_key.pub
    $ ssh-keygen -i -f my_ssh_key.pub > .ssh/my_ssh_key.pub
    $ cd .ssh/
    $ ll
    $ cat my_ssh_key.pub
    $ cat authorized_keys
    $ vim authorized_keys
    $ cd ~
    $ sudo reboot
