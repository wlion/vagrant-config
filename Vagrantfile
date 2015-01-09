Vagrant.configure("2") do |config|
	config.vm.box = "hashicorp/precise32"
	config.vm.provision :shell, path: "bootstrap.sh"
	config.vm.provision :shell, path: "adb.sh", run: "always"
	config.vm.network :forwarded_port, host: 8100, guest: 8100
	config.ssh.forward_agent = true

	config.vm.provider "virtualbox" do |vb|
    	vb.customize ["modifyvm", :id, "--usb", "on"]
    	vb.customize ['usbfilter', 'add', '0', '--target', :id, '--name', 'T01130CWSX', '--vendorid', '0x22b8']
    	vb.customize ["usbfilter", "add", "0", "--target", :id, "--name", "android", "--vendorid", "0x18d1"]
    end
end