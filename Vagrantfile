#Vagrant::Config.run do |config|
Vagrant.configure("2") do |config|
  config.vm.define :devel do |devel_config|
	devel_config.vm.box = "centos64"
	devel_config.vm.hostname = "devel"
	devel_config.ssh.max_tries = 100
	#devel_config.vm.boot_mode = :gui
	devel_config.vm.provider :virtualbox do |devel_vb|
    		devel_vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50", "--memory", "1024", "--ioapic", "on"]
  	end
	devel_config.vm.network :private_network, ip: "192.168.90.2"
	devel_config.vm.provision :puppet do |devel_puppet|
		devel_puppet.pp_path = "/tmp/vagrant-puppet"
		devel_puppet.manifests_path = "manifests"
		devel_puppet.module_path = "modules"
		devel_puppet.manifest_file = "site.pp"
		devel_puppet.options = "--verbose"
	end
  end
  config.vm.define :prod do |prod_config|
	prod_config.vm.box = "centos64"
	prod_config.vm.hostname = "prod"
	prod_config.ssh.max_tries = 100
	#devel_config.vm.boot_mode = :gui
	prod_config.vm.provider :virtualbox do |prod_vb|
    		prod_vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50", "--memory", "1024", "--ioapic", "on"]
  	end
	prod_config.vm.network :private_network, ip: "192.168.90.3"
	prod_config.vm.provision :puppet do |prod_puppet|
		prod_puppet.pp_path = "/tmp/vagrant-puppet"
		prod_puppet.manifests_path = "manifests"
		prod_puppet.module_path = "modules"
		prod_puppet.manifest_file = "site.pp"
		prod_puppet.options = "--verbose"
	end
  end
end
