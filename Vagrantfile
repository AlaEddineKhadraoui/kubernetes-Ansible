















Vagrant.configure("2") do |config|
  
    
  
  
#setting up  a virtual machine for k8s master  
  config.vm.define "k8s_master" do |master|
        master.vm.box = "centos/7"
        master.vm.network "private_network", ip: "192.168.121.10"
        master.vm.hostname = "master"
        master.vm.provider "libvirt" do |v|
           v.cpus = 2
           v.memory = 2048
        end
        
        
        
        master.vm.provision "ansible" do |ansible|
            ansible.playbook = "master.yml"
           
        end
   
   end

N=3

#setting up a virtual machines for K8s workers
    (1..N).each do |i|
        config.vm.define "worker#{i}" do |node|
            node.vm.box = "centos/7"
            node.vm.network "private_network", ip: "192.168.121.#{i + 10}"
            node.vm.hostname = "worker#{i}"
            node.vm.provider "libvirt" do |v|
              v.cpus = 1
              v.memory = 1024
            end
            
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "worker.yml"
              
            end
        end
    end
end
 


