Vagrant.configure("2") do |config|
    config.vm.box = "precise64"
    config.vm.box_url = "http://files.vagrantup.com/precise64.box"
    config.vm.network :private_network, ip: "192.168.33.101"
    config.vm.network "forwarded_port", guest: 35729, host: 35729
    config.vm.network "forwarded_port", guest: 3000, host: 3000
    config.vm.synced_folder "./", "/vagrant", id: "vagrant-root"
    config.vm.provision :shell, :path => "scripts/welcome.sh"
    # config.vm.provision :shell, :inline => "echo Hello, World"

    config.vm.provision :puppet do |puppet|
      puppet.manifests_path = "puppet/manifests"
      puppet.module_path    = "puppet/modules"
      puppet.options        = ['--verbose']
    end
end