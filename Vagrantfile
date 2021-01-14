# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # THE VAGRANT SOURCE BASE BOX 
  config.vm.box = "generic/rhel8"

  # NAME THE VM SO WE CAN IDENTIFY IT
  config.vm.define "rhelbuilds"
  config.vm.hostname = "rhelbuilds"

  # DISKS
  # use this via the vagrant-disksize plugin to increase the default primary disk size:
  #config.disksize.size = '200GB'

  # use this via the vagrant-persistent-storage plugin to add other disks
  config.persistent_storage.enabled = true
  config.persistent_storage.diskdevice = '/dev/sdb'
  config.persistent_storage.location = "datadisk.vdi"
  config.persistent_storage.size = 20000
  config.persistent_storage.mountname = 'data'
  config.persistent_storage.filesystem = 'ext4'
  config.persistent_storage.mountpoint = '/data'
  config.persistent_storage.volgroupname = 'datavg'

  # NETWORKING - gets DHCP address from my local net
  config.vm.network "public_network", bridge: "en0: Wi-Fi (Wireless)"

  # SHARED HOST FOLDER
  config.vm.synced_folder "~/Downloads", "/vagrant_data"

  # RHSM BITS using the vagrant-registration plugin
  config.registration.username = ENV['SUB_USERNAME']
  config.registration.password = ENV['SUB_PASSWORD']
  #config.registration.pools = ['pool1', 'pool2']
  config.registration.unregister_on_halt = false

  # VM CUSTOMISATIONS
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.name = "rhelbuilds"
    vb.memory = "2048"
    vb.cpus = "2"
  end

end
