This contains complete generalized puppet script for installing latest APACHE, MYSQL & PHP on all Linux Operating Systems
*******************************************************************************************

Server Configuration Management Setup
=====================================


For rpm package: (redhat,centos, etc)
-------------------------------------

su -c 'rpm -Uvh http://download.fedora.redhat.com/pub/epel/5/i386/epel-release-5-4.noarch.rpm'
wget http://rpms.famillecollet.com/enterprise/remi-release-5.rpm
rpm -Uvh remi-release-5*.rpm
sed -i 's/enabled=0/enabled=1/' /etc/yum.repos.d/remi.repo
yum install git-core puppet

cd $HOME
ssh-keygen -t rsa 
vi .ssh/id_rsa.pub

Paste the ssh key into the GitHub account you'll be using

sudo git clone git@github.com:geopcgeo/LAMP.git

mkdir /etc/puppet/modules
mkdir /etc/puppet/manifests
cp -Rv LAMP/* /etc/puppet/modules
cp /etc/puppet/modules/nodes.pp /etc/puppet/manifests/
puppet -v /etc/puppet/manifests/nodes.pp
init 6


For debian package: (ubuntu, debian etc)
----------------------------------------

sudo apt-get install -y git-core puppet

cd $HOME
sudo ssh-keygen -t rsa 
sudo vi .ssh/id_rsa.pub

Paste the ssh key into the GitHub account you'll be using

sudo git clone git@github.com:geopcgeo/LAMP.git

sudo mkdir /etc/puppet/modules
sudo mkdir /etc/puppet/manifests
sudo cp -Rv LAMP/* /etc/puppet/modules
sudo cp /etc/puppet/modules/nodes.pp /etc/puppet/manifests/
sudo puppet -v /etc/puppet/manifests/nodes.pp
sudo reboot

Thats all! :)
