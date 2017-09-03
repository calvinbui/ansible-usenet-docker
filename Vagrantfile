Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.define "ansible-usenet-docker"

    # Networking
    config.vm.network "private_network", ip: "172.16.0.2"
    config.vm.network "forwarded_port", guest: 80, host: 80 # nginx
    config.vm.network "forwarded_port", guest: 6789, host: 6789 # nzbget
    config.vm.network "forwarded_port", guest: 8989, host: 8989 # sonarr
    config.vm.network "forwarded_port", guest: 5050, host: 5050 #couchpotato
    config.vm.network "forwarded_port", guest: 5075, host: 5075 # nzbhydra
    config.vm.network "forwarded_port", guest: 9091, host: 9091 # transmission

    # Install Ansible locally
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install software-properties-common -y
      sudo apt-add-repository ppa:ansible/ansible
      sudo apt-get update
      sudo apt-get install ansible -y
    SHELL

    # Copy the vault password over
    config.vm.provision "file", source: "vault.txt", destination: "/tmp/vault.txt"

    # Run Ansible Playbook locally
    config.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "site.yml"
      ansible.vault_password_file = "/tmp/vault.txt"
      # Add this VM to the 'vagrant' group to use the vagrant group_vars
      ansible.groups = {
        "vagrant" => ["ansible-usenet-docker"]
      }
    end

end
