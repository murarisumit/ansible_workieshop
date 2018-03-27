# -*- mode: ruby -*-
# vi: set ft=ruby :
# This file is used for local development only.
#
# To setup it up use make convenience commands like:
#  make web or make web-stage

groups = {
  "webservers" => ["web", "web_stage"],
  "celery" => ["celery", "celery_stage"],
}

Vagrant.configure("2") do |config|
  config.vm.define :demo do |demo|
    # ansible_inventory_dir = "hosts/vagrant-prod"
    ansible_inventory_dir = "hosts"
    demo.vm.box = "ubuntu/xenial64"
    demo.vm.box_check_update = false
    demo.vm.network "private_network", ip: "192.168.111.122"
    demo.vm.provision "ansible" do |ansible|
      ansible.playbook = "first_playbook.yml"
      #ansible.verbose        = true
      ansible.limit          = "all" # or only "nodes" group, etc.
      # ansible.inventory_path = "#{ansible_inventory_dir}/inventory"
      ansible.inventory_path = "#{ansible_inventory_dir}"
      ansible.groups = groups
    end
  end
end
