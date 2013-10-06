# Vagrant Precise Pangolin 12.04 64-bit Box Setup

### Dependencies:

> Oracle VM Box

### Objectives:

* Download Vagrant Package
* Add Box
* Initialize the Box
* Start the VM
* SSH to the VM
* Install Ruby and Git
* Port Fordwarding
* Apply Forwarded Port
* vagrant -help

### Download Vagrant package as per your system from below link

```
http://downloads.vagrantup.com/tags/v1.3.4
```

### Add Box

```
vagrant box add precise64 http://files.vagrantup.com/precise64.box
```

### Initialize the Box

```
vagrant init precise64
```

### Start the VM

```
vagrant up
```

SSH to VM

```
vagrant ssh
```

### Install Ruby and Git using postinstall script

* Once inside the VM the run the ls command to list the postinstall script

```
ls
```

> **Note:** You will find a Postinstall script. Open the script and do the following change

```
sudo nano postinstall.sh
```

> Edit the ruby version

```
ruby_ver="2.0.0p247"
```

> Save the changes by ctrl+x and run the following command to execute the script

```
sudo ./postinstall.sh
```

### Port Fordwarding

> On your local machine, the directory where vagrant was installed, you will find a Vagrantfile

* Port forwarding is specified in the Vagrantfile, like so:

```
Vagrant::Config.run do |config|
  # Forward guest port 80 to host port 4567
  config.vm.forward_port 80, 4567
end
```

* forward_port is a method which takes two arguments:

> guest port - The port on the virtual machine.

> host port - The port on your local machine you want to use to access the guest port.

* Apply Forwarded Port

### Reload Vagrant

```
vagrant reload
```

### Start the VM again

```
vagrant up
```

### vagrant -help

Usage: vagrant [-v] [-h] command [<args>]

```
    -v, --version                    Print the version and exit.
    -h, --help                       Print this help.

Available subcommands:
     box
     destroy
     gem
     halt
     init
     package
     provision
     reload
     resume
     ssh
     ssh-config
     status
     suspend
     up

For help on any individual command run `vagrant COMMAND -h`
```

References:

* http://docs-v1.vagrantup.com/v1/docs/getting-started/
* http://docs-v1.vagrantup.com/v1/docs/getting-started/boxes.html
* http://docs-v1.vagrantup.com/v1/docs/getting-started/ssh.html
* http://docs-v1.vagrantup.com/v1/docs/getting-started/ports.html

List of all Vagrant Boxes

* http://www.vagrantbox.es/
