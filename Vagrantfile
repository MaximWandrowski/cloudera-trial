ENV["LC_ALL"] = "en_US.UTF-8"

Vagrant.configure("2") do |config|
  (1..3).each do |i|
    config.vm.define "cloudera#{i}" do |node|
      node.vm.box      = "hashicorp/bionic64"
      node.vm.hostname = "cloudera#{i}"
      node.vm.disk "disk", size: "64GiB"
      node.vm.network  "private_network", ip: "10.0.0.1#{i}"
      node.vm.provider "virtualbox" do |v|
        v.name   = "cloudera#{i}"
        v.memory = 8192
        v.cpus   = 8
      end
    end
  end
end
