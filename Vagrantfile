# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'.freeze

# system "vagrant plugin update"
# required_plugins = %w(vagrant-digitalocean)
# required_plugins.each do |plugin|
#   system "NOKOGIRI_USE_SYSTEM_LIBRARIES=1 vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
# end

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.define 'tmux' do |tmux|
    tmux.vm.hostname = 'tmux'
#    tmux.vm.network 'private_network', ip: '33.33.33.44'
    tmux.vm.network "public_network"
    tmux.vm.provider 'virtualbox' do |provider|
      provider.name = 'tmux'
      provider.customize ['modifyvm', :id, '--memory', '512']
    end

    tmux.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'playbook.yml'
      ansible.inventory_path = 'inventory'
      ansible.host_key_checking = false
      ansible.sudo = true
    end
  end

end

