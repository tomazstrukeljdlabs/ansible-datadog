# -*- mode: ruby -*-
# vi: set ft=ruby :

BOX_LABEL="ansible-role-datadog"
BOX_IP="10.10.0.80"

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    # All Vagrant configuration is done here. The most common configuration
    # options are documented and commented below. For a complete reference,
    # please see the online documentation at vagrantup.com.

    # Every Vagrant virtual environment requires a box to build off of.
    config.vm.box = "ubuntu/trusty64"
    config.vm.network :private_network, ip: BOX_IP

    config.vm.provider :virtualbox do |v|
        v.name = BOX_LABEL
        v.customize [
            "modifyvm", :id,
            "--name", BOX_LABEL,
            "--memory", 1024,
            "--natdnshostresolver1", "on",
            "--natdnsproxy1", "on",
            "--cpus", 2,
        ]
    end

    config.vm.provision :ansible do |ansible|
        ansible.playbook = "test.yml"
        ansible.sudo = true
        ansible.verbose =  'vvvv'
    end
end
