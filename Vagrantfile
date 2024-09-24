VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Define number of nodes
  num_nodes = 2

  # Configure base IP and subnet mask (adjust as needed)
  base_ip = "192.168.0"
  subnet_mask = "255.255.255.0"

  (1..num_nodes).each do |i|
    # Calculate IP address for each node (assuming sequential numbering)
    ip_address = "#{base_ip}.#{i}0"

    config.vm.define "soufe#{i}" do |node|  # Change to soufe#{i}
      node.vm.box = "rockylinux/9"
      node.vm.hostname = "soufe#{i}"

      # Configure private network with static IP
      node.vm.network "private_network", ip: ip_address, netmask: subnet_mask

      # Configure Ansible provisioning
      node.vm.provision "ansible" do |ansible|
        ansible.become = true
        ansible.playbook = "ansible/playbook.yml"
        ansible.inventory_path = "ansible/inventory"
        ansible.compatibility_mode = "2.0"
      end
    end
  end
end

