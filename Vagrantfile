#require 'vagrant-aws'
Vagrant.configure("2") do |config|
   config.vm.box = 'dummy'
   config.vm.define "aws" do | config_aws|
   config_aws.vm.provider 'aws' do |aws, override|
   aws.access_key_id = "#######"
   aws.secret_access_key = "#######"
   aws.keypair_name = 'docker'
   aws.instance_type = "t2.micro"
   aws.region = 'ap-south-1'
   aws.ami = 'ami-5d99ce32'
   aws.security_groups = ['newsecgrp']
   aws.tags = {
          'Name' => 'tomcat'
   }
   override.ssh.username = 'centos'
   override.ssh.private_key_path = '~/.ssh/docker.pem'
   end
   config.vm.provision "ansible" do |ansible|
   ansible.verbose = "v"
   ansible.playbook = "tomcat.yml"
   ansible.host_key_checking = false
   ansible.limit = 'aws'
end
end
   config.vm.box = 'dummy'
   config.vm.define "aws1" do | config_aws1|
   config_aws1.vm.provider 'aws' do |aws1, override|
   aws1.access_key_id = "#########"
   aws1.secret_access_key = "###########"
   aws1.keypair_name = 'docker'
   aws1.instance_type = "t2.micro"
   aws1.region = 'ap-south-1'
   aws1.ami = 'ami-5d99ce32'
   aws1.security_groups = ['newsecgrp']
   aws1.tags = {
         'Name' => 'maven-tomcat'
   }
   override.ssh.username = 'centos'
   override.ssh.private_key_path = '~/.ssh/docker.pem'
   end
   config.vm.provision "ansible" do |ansible|
   ansible.verbose = "v"
   ansible.playbook = "maven_tomcat.yml"
   ansible.host_key_checking = false
   ansible.limit = 'aws1'
end
end
end   
