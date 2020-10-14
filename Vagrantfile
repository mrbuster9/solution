# -*- mode: ruby -*-
# vi: set ft=ruby :
$script = <<~SCRIPT
apt-get install -y ansible
SCRIPT
Vagrant.configure("2") do |config|

    config.vm.box = 'debian/jessie64'
    config.vm.provider :virtualbox do |vb|
        vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
    end

    config.vm.define 'web' do |web|
	web.vm.provision "shell",
    inline: "apt-get install -y apache2 ansible"
        web.vm.network 'private_network', ip: '192.168.2.31'
        ENV['LC_ALL']='en_US.UTF-8'
    end

    config.vm.define 'db' do |db|
	db.vm.provision "shell", inline: $script
        db.vm.network 'private_network', ip: '192.168.2.32'
        ENV['LC_ALL']='en_US.UTF-8'
    end 
   
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "recreate.yml"
    end

end
