if Vagrant::VERSION < "2.0.0"
  $stderr.puts "Must redirect to new repository for old Vagrant versions"
  Vagrant::DEFAULT_SERVER_URL.replace('https://vagrantcloud.com')
end

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.box_check_update = false
  config.vm.synced_folder "shared/", "/shared", create: true
  config.vm.synced_folder "dataset/", "/dataset", create: true
  config.vm.network "forwarded_port", guest: 30000, host: 30000
  config.vm.network "forwarded_port", guest: 30001, host: 30001
  config.vm.network "forwarded_port", guest: 30002, host: 30002

  config.vm.define "Mongo40" do |server|
    server.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "Mongo40"
      vb.memory = 4096
    end
    server.vm.hostname = "mongo40.mongodb.university"
    server.vm.network :private_network, ip: "192.168.14.100"
    config.vm.provision "shell", inline: "echo 'export MONGO_VERSION=#{ENV['MONGO_VERSION']}' > /etc/profile.d/myvars.sh", run: "always"
    server.vm.provision :shell, path: "provision-mongodb", args: ENV['ARGS']
  end
end
