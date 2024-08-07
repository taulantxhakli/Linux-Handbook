# QEMU KVM Virtualization

This guide is assuming KVM and other virtualization settings are enabled in your BIOS. 

- Note: You might need to enable IOMMU for Windows VM's that require GPU passthrough


```
sudo pacman -S qemu-full virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat iptables ebtables libguestfs
```

Once installed, enable and start libvirtd:

```
sudo systemctl enable libvirtd.service
```

```
sudo systemctl start libvirtd.service
```

To check if the virsh net has started, list in the command:

```
sudo virsh net-list --all
```

If not, start the default network:

```
sudo virsh net-autostart default
```

The virt-manager should now be on the system and able to start virtualizations.

When not using the VM, the network can be stopped by:

```
sudo virsh net-destroy default
```

If using this to create a Windows 11 VM and do not want to passthrough a physical TPM 2.0 chip:

```
sudo pacman -S swtpm
```
