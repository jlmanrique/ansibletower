if Vagrant::VERSION < "2.0.0"
  $stderr.puts "Must redirect to new repository for old Vagrant versions"
  Vagrant::DEFAULT_SERVER_URL.replace('https://vagrantcloud.com')
end

Vagrant.configure("2") do |config|
  config.vm.box = "ansible/tower"
  config.vm.box_check_update = false

  config.vm.define "ansible-demo-test" do |server|
    server.vm.provider "virtualbox" do |vb|
	     vb.customize ["modifyvm", :id, "--cpus", "2"]
       vb.name = "ansible-demo"
       vb.memory = 4096
    end
    server.vm.hostname = "ansible-demo"
    server.vm.provision :shell, path: "add-valid-cert", args: ENV['ARGS']
  end

end
