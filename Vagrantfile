
servers = [
  {
    ### Jenkins Server ###
    :hostname => "jenkins-server",
    :box => "ubuntu/bionic64",
    :ip => "10.3.20.17",
    :memory => "2048",
    :cpu => "2",
    :vmname => "JenkinsServer",
    :script => "./configurations/jenkins.sh"
  },
  {
    ### Nexus Server ###
    :hostname => "nexus-server",
    :box => "geerlingguy/centos7",
    :ip => "10.3.20.18",
    :memory => "2048",
    :cpu => "2",
    :vmname => "NexusServer",
    :script => "./configurations/nexus.sh"
  },
  {
    ### Sonarqube Server ###
    :hostname => "sonar-server",
    :box => "ubuntu/bionic64",
    :ip => "10.3.20.19",
    :memory => "2048",
    :cpu => "2",
    :vmname => "SonarServer",
    :script => "./configurations/sonar.sh"
  }
]

Vagrant.configure("2") do |config|
  # manages the /etc/hosts file on guest machines in multi-machine environments
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true

  servers.each do |machine|
    config.vm.define machine[:hostname] do |node|
      node.vm.box = machine[:box]
      node.vm.hostname = machine[:hostname]
      node.vm.network :private_network, ip: machine[:ip]

      node.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--name", machine[:vmname]]
        vb.customize ["modifyvm", :id, "--memory", machine[:memory]]
        vb.customize ["modifyvm", :id, "--cpus", machine[:cpu]]

        
      end

      node.vm.provision "shell", path: File.join(File.dirname(__FILE__), machine[:script])
    end
  end
end



