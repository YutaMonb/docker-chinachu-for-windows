Vagrant.configure(2) do |config|
  config.vm.define "chinachu"

  config.vm.box = "ubuntu/xenial64"

  config.vm.synced_folder ".", "/vagrant"
  
  config.vm.network "forwarded_port", guest: 10772, host: 10772
  config.vm.network "forwarded_port", guest: 20772, host: 20772
  config.vm.network "forwarded_port", guest: 5353, host: 5353, protocol: "udp"

  config.vm.provider :virtualbox do |vb|
    vb.customize [
      "modifyvm", :id,
      "--hwvirtex", "on",
      "--nestedpaging", "on",
      "--largepages", "on",
      "--memory", "4096",
      "--cpus", "4",
      "--ioapic", "on",
      "--pae", "on",
      "--paravirtprovider", "kvm"
    ]
  end

  if ARGV[0] == "up" || ARGV[0] == "provision" then
    config.vm.provision :shell do |shell|
      shell.inline = <<-SHELL
        sudo apt update && \
        sudo apt install \
          apt-transport-https \
          ca-certificates \
          curl \
          software-properties-common -y && \
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && \
        sudo apt-key fingerprint 0EBFCD88 && \
        sudo add-apt-repository \
          "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
          $(lsb_release -cs) \
          stable" && \
        sudo apt update && sudo apt install docker-ce docker-compose -y && \
        cd /vagrant && sudo docker-compose up -d && \
        echo "SUCCESS!!!!!!"
      SHELL
      shell.privileged = false
    end
  end
end
