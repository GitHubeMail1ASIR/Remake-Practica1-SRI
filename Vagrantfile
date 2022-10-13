Vagrant.configure("2") do |config|

config.vm.define :router do |router|
    router.vm.box = "debian/bullseye64"
    router.vm.hostname = "router"
    router.vm.synced_folder ".", "/vagrant", disabled: true
    router.vm.network :public_network,
      :dev => "br0",
      :mode => "bridge",
      :type => "bridge",
      use_dhcp_assigned_default_route: true
    router.vm.network :private_network,
      :libvirt__network_name => "muy-aislada",
      :libvirt__dhcp_enabled => false,
      :ip => "10.0.0.1",
      :libvirt__forward_mode => "veryisolated"
  end
  config.vm.define :cliente do |cliente|
    cliente.vm.box = "debian/bullseye64"
    cliente.vm.hostname = "cliente"
    cliente.vm.synced_folder ".", "/vagrant", disabled: true
    cliente.vm.network :private_network,
      :libvirt__network_name => "muy-aislada",
      :libvirt__dhcp_enabled => false,
      :ip => "10.0.0.2",
      :libvirt__forward_mode => "veryisolated"
  end
end