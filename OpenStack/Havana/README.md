CentOS KickStart
==========

CentOS 6 kickstart file with minimal stuff and the extras that needed to make an OpenStack CentOS Image. Included in %post is a bit to resize the root filesystem to the size of the actual device provided to the VM.

Create base image with virt-install:

sudo virt-install --name CentOS-6-x86_64 --ram 1024 --cpu host --vcpus 1 --nographics --os-type=linux --os-variant=rhel6 --location=http://mirrors.kernel.org/centos/6/os/x86_64 --initrd-inject=CentOS-6-x86_64.ks --extra-args="ks=file:/CentOS-6-x86_64.ks text console=tty0 utf8 console=ttyS0,115200" --disk path=/var/lib/libvirt/images/CentOS-6-x86_64.img,size=2,bus=virtio --force --noreboot


Point to the bridge with external connectivity if it is not eth0:

--network=bridge=br0
