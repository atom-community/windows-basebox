# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "windows"
  config.vm.box_check_update = false

  config.vm.provider :vmware_fusion do |v, override|
      v.gui = true
      v.vmx["memsize"] = "2048"
      v.vmx["numvcpus"] = "2"
      v.vmx["ethernet0.virtualDev"] = "vmxnet3"
      v.vmx["RemoteDisplay.vnc.enabled"] = "false"
      v.vmx["RemoteDisplay.vnc.port"] = "5900"
      v.vmx["scsi0.virtualDev"] = "lsisas1068"
  end

  config.vm.provision "shell", inline: "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))"
  config.vm.provision "shell", inline: "choco install -y 7zip git python2"
  config.vm.provision "shell", path: "scripts/install-nvm.ps1"
  config.vm.provision "shell", path: "scripts/install-node.ps1"
  config.vm.provision "shell", inline: "choco install -y visualstudio2015community"
end