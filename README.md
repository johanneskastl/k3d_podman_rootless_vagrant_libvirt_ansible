# k3d_podman_rootless_vagrant_libvirt_ansible

This Vagrant setup creates a VM and installs
[k3d](https://github.com/k3d-io/k3d) and rootless Podman.

Default OS is openSUSE Leap 15.5. Although that can be changed in the
Vagrantfile, please beware that this will break the Ansible provisioning.

## Vagrant

1. You need vagrant obviously. And ansible. And git...
1. Fetch the box, per default this is `opensuse/Leap-15.5.x86_64`, using
   `vagrant box add opensuse/Leap-15.5.x86_64`.
1. Make sure the git submodules are fully working by issuing `git submodule init
   && git submodule update`
1. Run `vagrant up`
1. Connect to the VM with `vagrant ssh k3d`.
1. Have fun with k3d.
1. Party!

## Cleaning up

The VMs can be torn down after playing around using `vagrant destroy`.

## Disabling the Ansible provisioning

In case you do not want Ansible to install k3d (because you want to
install it yourself), just comment out the following lines in the `Vagrantfile`:

```hcl
    node.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
        ansible.limit = "all"
      ansible.playbook = "ansible/playbook-vagrant.yml"
    end # node.vm.provision
```

You also find all of the playbooks in the `ansible` folder.

## License

BSD-3-Clause

## Author Information

I am Johannes Kastl, reachable via git@johannes-kastl.de
