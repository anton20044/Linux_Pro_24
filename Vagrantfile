# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos8"


  config.vm.provider "virtualbox" do |v|
	  v.memory = 1536
  end

  config.vm.define "ns01" do |ns01|
    ns01.vm.network "private_network", ip: "192.168.56.10", virtualbox__intnet: "dns"
    ns01.vm.network "private_network", ip: "192.168.57.10"
    ns01.vm.hostname = "ns01"
    ns01.vm.provision "shell", inline: <<-SHELL
          sudo sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
          sudo sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
          sed -i 's/^PasswordAuthentication.*$/PasswordAuthentication yes/' /etc/ssh/sshd_config
          systemctl restart sshd.service
      SHELL
    ns01.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.become = "true"
  end


  end

  config.vm.define "ns02" do |ns02|
    ns02.vm.network "private_network", ip: "192.168.56.11", virtualbox__intnet: "dns"
    ns02.vm.network "private_network", ip: "192.168.57.11"    
    ns02.vm.hostname = "ns02"
    ns02.vm.provision "shell", inline: <<-SHELL
          sudo sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
          sudo sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
          sed -i 's/^PasswordAuthentication.*$/PasswordAuthentication yes/' /etc/ssh/sshd_config
          systemctl restart sshd.service
      SHELL
    ns02.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.become = "true"
  end

  end

  config.vm.define "client" do |client|
    client.vm.network "private_network", ip: "192.168.56.15", virtualbox__intnet: "dns"
    client.vm.network "private_network", ip: "192.168.57.15"
    client.vm.hostname = "client"
    client.vm.provision "shell", inline: <<-SHELL
          sudo sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
          sudo sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
          sed -i 's/^PasswordAuthentication.*$/PasswordAuthentication yes/' /etc/ssh/sshd_config
          systemctl restart sshd.service
      SHELL
    client.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.become = "true"
  end


  end

  config.vm.define "client2" do |client2|
    client2.vm.network "private_network", ip: "192.168.56.25", virtualbox__intnet: "dns"
    client2.vm.network "private_network", ip: "192.168.57.25"
    client2.vm.hostname = "client2"
    client2.vm.provision "shell", inline: <<-SHELL
          sudo sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
          sudo sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
          sed -i 's/^PasswordAuthentication.*$/PasswordAuthentication yes/' /etc/ssh/sshd_config
          systemctl restart sshd.service
      SHELL
    
    client2.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.become = "true"
  end
 end
end
