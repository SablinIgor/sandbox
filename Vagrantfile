$script = <<-SCRIPT
echo "!!! Install ansible... !!!"
sudo yum install epel-release -y
sudo yum -y update
sudo yum install ansible unzip git vim tree -y
sudo yum -y install python-pip pip

echo "!!! Install packer... !!!"
curl -L -O https://releases.hashicorp.com/packer/1.4.0/packer_1.4.0_linux_amd64.zip
unzip packer_1.4.0_linux_amd64.zip
mv packer /usr/local/bin/
rm packer_1.4.0_linux_amd64.zip

echo "!!! Install terraform... !!!"
curl -L -O https://releases.hashicorp.com/terraform/0.11.13/terraform_0.11.13_linux_amd64.zip
unzip terraform_0.11.13_linux_amd64.zip
mv terraform /usr/local/bin/
rm terraform_0.11.13_linux_amd64.zip

echo # vagrant profile script > /etc/profile.d/vagrant.sh
echo export GOOGLE_APPLICATION_CREDENTIALS="~/gcp-secret-key.json" >> /etc/profile.d/vagrant.sh
chmod +x /etc/profile.d/vagrant.sh

echo "!!! Install gcloud... !!!"
sudo tee -a /etc/yum.repos.d/google-cloud-sdk.repo << EOM
[google-cloud-sdk]
name=Google Cloud SDK
baseurl=https://packages.cloud.google.com/yum/repos/cloud-sdk-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
       https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOM

yum install google-cloud-sdk -y

SCRIPT

Vagrant.configure("2") do |config|
    config.vm.box = "centos/7"
    config.vm.synced_folder "../../SablinIgor_infra/", "/home/vagrant/otus"

    config.vm.provision "shell", inline: $script
    config.vm.provision "file", source: "~/.ssh/ubuntu", destination: "/home/vagrant/.ssh/ubuntu"
    config.vm.provision "file", source: "~/.ssh/ubuntu.pub", destination: "/home/vagrant/.ssh/ubuntu.pub"
    config.vm.provision "file", source: "~/SablinIgor_infra/infra-234615-9e270e79d2c8.json", destination: "/home/vagrant/gcp-secret-key.json"
end
