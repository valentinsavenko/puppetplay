Vagrant.configure("2") do |config|
  # Define the Puppet targets
  (1..2).each do |i|
    config.vm.define "puppet-target#{i}" do |puppet_target|
      puppet_target.vm.box = "ubuntu/bionic64"
      puppet_target.vm.network "private_network", ip: "192.168.33.10"
      puppet_target.vm.synced_folder ".", "/vagrant"
      puppet_target.vm.provision :docker
      puppet_target.vm.provision :docker_compose, yml: "/vagrant/docker-compose-targets.yml", run: "always"
      # puppet_target1.vm.network "forwarded_port", guest: 8080, host: 8080
      # puppet_target1.vm.network "forwarded_port", guest: 8140, host: 8140
      # puppet_target1.vm.network "forwarded_port", guest: 8088, host: 8088
      
      # add hosts file entries
      # TODO make the network usage between docker and vagrant work
      puppet_target.vm.provision "shell", inline: <<-SHELL
        echo '192.168.0.180 puppet' >> /etc/hosts
      SHELL
    end
  end
end
  # config.vm.define "puppet-target2" do |puppet_target2|
  #  puppet_target2.vm.box = "ubuntu/bionic64"
  #  puppet_target2.vm.network "private_network", ip: "192.168.33.11"
  #  puppet_target2.vm.synced_folder "./vagrant-shared", "/vagrant/vagrant-shared"
  # #  puppet_target2.vm.provision "puppet_apply" do |puppet|
  # #    puppet.manifest_file = "/vagrant/vagrant-shared/manifests/init.pp"
  # #  end
  #  puppet_target2.vm.provision :docker
  #  puppet_target2.vm.provision :docker_compose, yml: "/vagrant/vagrant-shared/docker-compose-targets.yml", run: "always"
  # end
#  end
