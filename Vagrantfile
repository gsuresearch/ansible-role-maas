Vagrant.configure("2") do |config|

  config.vm.define "maas" do |box1|

    box1.vm.box = "peru/ubuntu-18.04-server-amd64"
    box1.vm.box_version = "20200806.01"

    box1.vm.provision :ansible do |ansible|
       ansible.playbook = 'test.yml'
       ansible.galaxy_role_file = "test-requirements.yml"
    end

    box1.vm.provider :libvirt do |domain|
      domain.memory = 4096
    end

  end

  config.vm.define :pxeclient1 do |pxeclient|
    pxeclient.vm.provider :libvirt do |domain|
      domain.storage :file, :size => '8G', :type => 'qcow2'
      domain.boot 'network'
      domain.boot 'hd'
      domain.memory = 1024
    end
  end

end
