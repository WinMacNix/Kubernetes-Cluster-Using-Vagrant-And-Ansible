nodes = [
  { :hostname => 'kubernetes-master',  :ip => '172.16.66.2', :ram => 2048 },
  { :hostname => 'kubernetes-node',  :ip => '172.16.66.3', :ram => 2048 }
]

Vagrant.configure("2") do |config|
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.box = "bento/ubuntu-16.04";
      nodeconfig.vm.hostname = node[:hostname] + ".box"
      nodeconfig.vm.network :private_network, ip: node[:ip]
      memory = node[:ram] ? node[:ram] : 256;
      nodeconfig.vm.provider :virtualbox do |vb|
        vb.customize [
          "modifyvm", :id,
          "--memory", memory.to_s,
          "--cpus", "2"
        ]
      end
    end
  end
end