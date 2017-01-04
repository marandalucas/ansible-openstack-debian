

Vagrant.configure("2") do |config|
  config.vm.define :openstack1 do |openstack1|
    openstack1.vm.box = "debian/contrib-jessie64"
    openstack1.vm.hostname = "openstack1"
    openstack1.vm.network "private_network", ip: "192.168.221.101"
    openstack1.vm.network :public_network, bridge: "enp2s0" ,ip: "172.18.65.233" # eth2 external
    openstack1.vm.provision "shell", inline: <<-SHELL
        echo  "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC746evYJbL/EGjrfgBHFXLAZVYhziNpCDLlRxegyFXEiTTIVWshVwRkSnqVIfGE/VCUwf72wz2MOwUt5R5qh6PTMMKSDFlUkV7D/eihk5tcJ7XXTvpeiXtB0QiqrsRoB3ZJX1AOIC5mUk/MwvX359iKlrr6tHzAHbdlErYl1eYoN0i5s8G4gJtzdkTm08j7nhpu9wRtuIgyUCrHCvCp/pz3DZXEwhAyv8ztigHNdBiDIIWF5L/0/MILZYTyKEgxdxTlM+4YVa9HTX8c3lpFwR7oVK6fdghc1qgBBB9bJfAqSJq92ZsjyWZyNNCZGDCm22Ydqk81/JExPwyHF3MAPs1 maranda@maranda-P552LA" >> /home/vagrant/.ssh/authorized_keys
        sudo su
        ssh-keygen -t rsa -N "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC746evYJbL/EGjrfgBHFXLAZVYhziNpCDLlRxegyFXEiTTIVWshVwRkSnqVIfGE/VCUwf72wz2MOwUt5R5qh6PTMMKSDFlUkV7D/eihk5tcJ7XXTvpeiXtB0QiqrsRoB3ZJX1AOIC5mUk/MwvX359iKlrr6tHzAHbdlErYl1eYoN0i5s8G4gJtzdkTm08j7nhpu9wRtuIgyUCrHCvCp/pz3DZXEwhAyv8ztigHNdBiDIIWF5L/0/MILZYTyKEgxdxTlM+4YVa9HTX8c3lpFwR7oVK6fdghc1qgBBB9bJfAqSJq92ZsjyWZyNNCZGDCm22Ydqk81/JExPwyHF3MAPs1 maranda@maranda-P552LA" -f ~/.ssh/id_rsa
        echo  "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC746evYJbL/EGjrfgBHFXLAZVYhziNpCDLlRxegyFXEiTTIVWshVwRkSnqVIfGE/VCUwf72wz2MOwUt5R5qh6PTMMKSDFlUkV7D/eihk5tcJ7XXTvpeiXtB0QiqrsRoB3ZJX1AOIC5mUk/MwvX359iKlrr6tHzAHbdlErYl1eYoN0i5s8G4gJtzdkTm08j7nhpu9wRtuIgyUCrHCvCp/pz3DZXEwhAyv8ztigHNdBiDIIWF5L/0/MILZYTyKEgxdxTlM+4YVa9HTX8c3lpFwR7oVK6fdghc1qgBBB9bJfAqSJq92ZsjyWZyNNCZGDCm22Ydqk81/JExPwyHF3MAPs1 maranda@maranda-P552LA" >> /root/.ssh/authorized_keys
    SHELL
    openstack1.vm.provider "virtualbox" do |vbox|
      vbox.customize ["modifyvm", :id, "--memory", "1098"]
      vbox.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"] # eth2
      vbox.customize ["createhd",
                  '--filename', "tmp/disk.vdi",
                  '--size', "3000" ]
      vbox.customize ['storageattach', :id,
                 '--storagectl', 'SATA Controller',
                 '--port', 1,
                 '--device', 0,
                 '--type', 'hdd',
                 '--medium', "tmp/disk.vdi"]
    end
  end
    config.vm.define :openstack2 do |openstack2|
      openstack2.vm.box = "debian/contrib-jessie64"
      openstack2.vm.hostname = "openstack2"
      openstack2.vm.network "private_network", ip: "192.168.221.102"
      openstack2.vm.provision "shell", inline: <<-SHELL
        echo  "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC746evYJbL/EGjrfgBHFXLAZVYhziNpCDLlRxegyFXEiTTIVWshVwRkSnqVIfGE/VCUwf72wz2MOwUt5R5qh6PTMMKSDFlUkV7D/eihk5tcJ7XXTvpeiXtB0QiqrsRoB3ZJX1AOIC5mUk/MwvX359iKlrr6tHzAHbdlErYl1eYoN0i5s8G4gJtzdkTm08j7nhpu9wRtuIgyUCrHCvCp/pz3DZXEwhAyv8ztigHNdBiDIIWF5L/0/MILZYTyKEgxdxTlM+4YVa9HTX8c3lpFwR7oVK6fdghc1qgBBB9bJfAqSJq92ZsjyWZyNNCZGDCm22Ydqk81/JExPwyHF3MAPs1 maranda@maranda-P552LA" >> /home/vagrant/.ssh/authorized_keys
        sudo su
        ssh-keygen -t rsa -N "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC746evYJbL/EGjrfgBHFXLAZVYhziNpCDLlRxegyFXEiTTIVWshVwRkSnqVIfGE/VCUwf72wz2MOwUt5R5qh6PTMMKSDFlUkV7D/eihk5tcJ7XXTvpeiXtB0QiqrsRoB3ZJX1AOIC5mUk/MwvX359iKlrr6tHzAHbdlErYl1eYoN0i5s8G4gJtzdkTm08j7nhpu9wRtuIgyUCrHCvCp/pz3DZXEwhAyv8ztigHNdBiDIIWF5L/0/MILZYTyKEgxdxTlM+4YVa9HTX8c3lpFwR7oVK6fdghc1qgBBB9bJfAqSJq92ZsjyWZyNNCZGDCm22Ydqk81/JExPwyHF3MAPs1 maranda@maranda-P552LA" -f ~/.ssh/id_rsa
        echo  "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC746evYJbL/EGjrfgBHFXLAZVYhziNpCDLlRxegyFXEiTTIVWshVwRkSnqVIfGE/VCUwf72wz2MOwUt5R5qh6PTMMKSDFlUkV7D/eihk5tcJ7XXTvpeiXtB0QiqrsRoB3ZJX1AOIC5mUk/MwvX359iKlrr6tHzAHbdlErYl1eYoN0i5s8G4gJtzdkTm08j7nhpu9wRtuIgyUCrHCvCp/pz3DZXEwhAyv8ztigHNdBiDIIWF5L/0/MILZYTyKEgxdxTlM+4YVa9HTX8c3lpFwR7oVK6fdghc1qgBBB9bJfAqSJq92ZsjyWZyNNCZGDCm22Ydqk81/JExPwyHF3MAPs1 maranda@maranda-P552LA" >> /root/.ssh/authorized_keys
    SHELL
      openstack2.vm.provider "virtualbox" do |vbox|
      vbox.customize ["modifyvm", :id, "--memory", "1048"]
    end
  end
end
