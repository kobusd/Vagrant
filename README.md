# Vagrant on Windows 10

[https://followkman.com/2016/07/27/vagrant-up-on-windows-10-with-hyper-v/]https://followkman.com/2016/07/27/vagrant-up-on-windows-10-with-hyper-v


## -Install Vagrant
[https://www.vagrantup.com/downloads.html]
(reboot after)

## -Install OpenSSH Client
(Required for ssh to work, or Authentication error)
### Download OpenSSH for Windows from:
[http://www.mls-software.com/opensshd.html]
After installing OpenSSH, download Vagrant public key using PowerShell:
PS> (Invoke-WebRequest -Uri https://raw.githubusercontent.com/mitchellh/vagrant/master/keys/vagrant.pub).Content >> “$env:USERPROFILE\.ssh/authorized_keys”
### Setup a private key:
PS>ssh-keygen
(Follow instructions, basically press enter a few times)
Force copy newly created private key over the Vagrant generated key:
PS> Copy-Item $env:USERPROFILE\.ssh\id_rsa $env:USERPROFILE\.vagrant.d\insecure_private_key -Force

## -Set default provider as Hyper-V
PS> $Env:VAGRANT_DEFAULT_PROVIDER = “hyperv”
Or set Vagrantfile default:
config.vm.provider “hyperv”
