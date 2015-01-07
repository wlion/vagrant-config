Vagrant.configure("2") do |config|
	config.vm.box = "hashicorp/precise32"
	config.vm.provision :shell, path: "bootstrap.sh"
	config.vm.network :forwarded_port, host: 8100, guest: 8100
	config.ssh.forward_agent = true
end