Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/trusty64"

    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install software-properties-common -y
      sudo apt-add-repository ppa:ansible/ansible
      sudo apt-get update
      sudo apt-get install ansible -y
    SHELL

    config.vm.provision "file", source: "vault.txt", destination: "/tmp/vault.txt"

    config.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "site.yml"
      ansible.vault_password_file = "/tmp/vault.txt"
    end

end
