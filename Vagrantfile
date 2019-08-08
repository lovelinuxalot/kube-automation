IMAGE_NAME = "debian/stretch64"
N = 2

Vagrant.configure("2") do |config|
    config.ssh.insert_key = true
    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 2
    end
     
    config.vm.define "master" do |master|
        master.vm.box = IMAGE_NAME
        master.vm.network "private_network", ip: "192.168.50.10"
        master.vm.hostname = "master"
    end

    config.vm.provision "shell" do |s|
    	ssh_pub_key = File.readlines("/home/allan/.ssh/id_rsa.pub").first.strip
    	s.inline = <<-SHELL
      	  echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
    	SHELL
    end

end

Vagrant.configure("2") do |config|
    config.ssh.insert_key = true
    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 1
    end

    (1..N).each do |i|
        config.vm.define "node#{i}" do |node|
            node.vm.box = IMAGE_NAME
            node.vm.network "private_network", ip: "192.168.50.#{i + 10}"
            node.vm.hostname = "node#{i}"
    	end
    end

    config.vm.provision "shell" do |s|
        ssh_pub_key = File.readlines("/home/allan/.ssh/id_rsa.pub").first.strip
        s.inline = <<-SHELL
          echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
        SHELL
    end 

end
