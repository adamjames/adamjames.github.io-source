Vagrant.configure("2") do |config|

  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"
  config.vm.synced_folder ".", "/vagrant", type: "rsync", rsync__exclude: "./_site/" 
  config.vm.network "forwarded_port", guest: 4000, host: 8124
  config.vm.provision :shell,
    :inline => "sudo apt-get update && sudo apt-get -y install build-essential git ruby1.9.3 nodejs && sudo gem install jekyll --no-ri --no-rdoc"

  config.ssh.forward_agent = true
end
