# PXE
PXE is a standard for booting machines over the network. In SOWN, this is used to allow servers to be remotely recovered or reinstalled - and avoiding needing to go to campus with a USB stick!

On boot, the NIC's PXE ROM will get an address via DHCP, then download via TFTP and boot iPXE. iPXE then chainloads a small script (sown.ipxe) which is used to fetch a kernel and initrd over HTTP.

The DHCP, TFTP and HTTP servers run on both of our GW servers. See the [ansible role](https://github.com/sown/ansible/tree/main/roles/pxe) for details. This also downloads an Ubuntu ISO and extracts the parts of the ISO needed for PXE boot.

## How?
See [our IPMI/iDRAC docs](idrac.md) for how to remotely get a console on servers.

During boot, do `<Escape><@>` repeatedly to get a machine to PXE boot.

## Building iPXE
We build our iPXE like:
```
apt install git build-essential liblzma-dev
git clone https://git.ipxe.org/ipxe.git
cd ipxe/src
echo "#define DIGEST_CMD" > config/local/general.h # enable md5sum+sha1sum
echo "#define CONSOLE_SERIAL" > config/local/console.h # enable serial console
make bin/undionly.kpxe
```

The DIGEST_CMD bit isn't needed now, we used to use it for validating image checksums by hand (when booting off public mirror servers).
