Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.5"
  config.vm.network "forwarded_port", guest: 80, host: 8084
  config.vm.network "public_network", ip: "192.168.0.115"

  ####### Install Puppet Agent #######
  config.vm.provision "shell", path: "./bootstrap.sh"

  ####### Hiera #######
  config.vm.synced_folder "hiera", "/tmp/vagrant-puppet/hiera"

  ####### Provision #######
  config.vm.provision "puppet" do |puppet|
    puppet.module_path = "./site"
    puppet.options = "--verbose --debug"
    puppet.hiera_config_path = "hiera.yaml"
    puppet.working_directory = "/tmp/vagrant-puppet/"
  end
end
