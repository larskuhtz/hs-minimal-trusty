# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.ssh.forward_agent = true

  config.vm.synced_folder ".", "/home/vagrant/hs-minimal-trusty"

  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
    v.cpus = 2
  end

  config.vm.provision "shell", inline: <<-SHELL
    which docker &>/dev/null || {
      curl -sSL https://get.docker.com/ubuntu/ | sudo sh
      sudo gpasswd -a vagrant docker
      sudo service docker restart
    }
  SHELL
end

