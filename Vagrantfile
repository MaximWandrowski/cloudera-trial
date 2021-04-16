ENV["LC_ALL"] = "en_US.UTF-8"

Vagrant.configure("2") do |config|
  N = 2
  (0..N-1).each do |i|
    config.vm.define "cloudera#{i}" do |node|
      node.vm.box      = "hashicorp/bionic64"
      node.vm.hostname = "cloudera#{i}"
      node.vm.disk "disk", size: "64GiB"
      node.vm.network  "private_network", ip: "10.0.0.#{10+i}"
      node.vm.provider "virtualbox" do |v|
        v.name   = "cloudera#{i}"
        v.memory = 12288
        v.cpus   = 8
      end
      if i == N-1
        node.vm.provision "ansible" do |ansible|
          ansible.limit = "all"
          ansible.playbook = "playbook.yml"
        end
      end
    end
  end
end
