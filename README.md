# Altschool_-Second_Semester_Examination
# NAME : ABUBAKAR AYOMIDE MICHEAAL 
# Student ID: ALT/SOE/023/2451
# Second Semester Project


STEP BY STEP DOCUMENTATION
This project was carried out using the following steps:
#        STEP 1
I have Installed Vagrant and VirtualBox.
I Created a new directory for my Vagrant project called project_altschool.
Inside the project directory, i created a Vagrantfile with the following content:

# (VAGRANTFILE)
Vagrant.configure("2") do |config|

  # Configure Master Node
  config.vm.define "master" do |master|
    master.vm.box = "ubuntu/focal64"
    master.vm.network "private_network", ip: "192.168.56.101"
    master.vm.hostname = "master"
    master.vm.provider "virtualbox" do |vb|
      vb.name = "Master"
      vb.memory = "1024"
    end
  end

  # Configure Slave Node
  config.vm.define "slave" do |slave|
    slave.vm.box = "ubuntu/focal64"
    slave.vm.network "private_network", ip: "192.168.33.12"
    slave.vm.hostname = "slave"
    slave.vm.provider "virtualbox" do |vb|
      vb.name = "Slave"
      vb.memory = "1024"
    end
  end

end
# Finally I vagrant up to start both virtual machines.


#           STEP TWO (Created a Bash Script for LAMP  on Master Node)
Inside the project directory,i created a file named lamp.sh.
find file in my resipitory
I made the script executable: chmod +x setup-lamp.sh.

#           STEP THREE (Provision Master VM with the Script)
I Ran vagrant reload --provision or vagrant provision to apply the script to the Master VM.

#           STEP FOUR (I Wrote Ansible Playbook for Slave Node)
I Installed Ansible on my PC(host Machine).
In the project directory,I created a file named playbook.yml.
Then i Update the Ansible inventory file with the IP of the Slave VM.
Lastly i Ran the playbook with ansible-playbook -i inventory playbook.yml.

#           Step Five: ( My Verification )
I SSH into the Slave VM: vagrant ssh slave.
I CheckED the application: Access the Slave VM's IP in MY web browser
I took a screenshot as evidence of the accessible application.
Finaly i verify the cron job: Ensure /var/log/uptime.log exists and has content after 12 am.

