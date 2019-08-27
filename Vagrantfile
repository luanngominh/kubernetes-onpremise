IMAGE_NAME = "centos/7"
N = 0

Vagrant.configure("2") do |config|
 
  config.vm.provider "virtualbox" do |v|
  end

  config.vm.define "k8s-master" do |master|
    master.vm.box = IMAGE_NAME
    master.vm.network "private_network", ip: "192.168.20.11"
    master.vm.hostname = "node01.k8s"
    config.disksize.size = "40GB"
    config.vm.provider "virtualbox" do |config|
      config.memory = 4096
      config.cpus = 2
    end
  end

  (2..N+1).each do |i|
    config.vm.define "node-#{i}" do |node|
        node.vm.box = IMAGE_NAME
        node.vm.network "private_network", ip: "192.168.20.#{i + 10}"
        node.vm.hostname = "node0#{i}.k8s"
        config.disksize.size = "40GB"
        config.vm.provider "virtualbox" do |config|
          config.memory = 2048
          config.cpus = 2
        end
    end

  end

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
