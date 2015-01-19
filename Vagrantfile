Vagrant.configure("2") do |config|
	config.vm.box = "hashicorp/precise32"
	config.vm.provision :shell, path: "bootstrap.sh"
	config.vm.provision :shell, path: "adb.sh", run: "always"
	config.vm.provision :shell, :inline => "echo -e '#{File.read("#{Dir.home}/.gitconfig")}' > '/home/vagrant/.gitconfig'"
	
	git_ssh_key = Dir.home << ".ssh/id_rsa"
	config.vm.provision :shell, :inline => "cat >> /home/vagrant/.ssh/id_rsa <<EOF #{git_ssh_key} EOF"
	
	config.vm.network :forwarded_port, host: 8100, guest: 8100
	config.vm.network :forwarded_port, host: 35729, guest: 35729
	config.ssh.forward_agent = true

	config.vm.provider "virtualbox" do |vb|
    	vb.customize ["modifyvm", :id, "--usb", "on"]
    	vb.customize ['usbfilter', 'add', '0', '--target', :id, '--name', 'T01130CWSX', '--vendorid', '0x22b8']
    	vb.customize ["usbfilter", "add", "0", "--target", :id, "--name", "android", "--vendorid", "0x18d1"]
    end
end