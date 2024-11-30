# iDRAC Access

## SSH Access

You can log into our iDRACs over SSH, via either of the GW servers.

For example:

```
me@login:~$ sudo ssh -J gw-b32 sown@vms-b32-1-ipmi
```

You can get a serial console with:
```
console com2
```
To exit the serial console, use control + `\`.

Useful shortcuts over serial:
```
KEY MAPPING FOR CONSOLE REDIRECTION:

Use the <ESC><1> key sequence for <F1>
Use the <ESC><2> key sequence for <F2>
Use the <ESC><3> key sequence for <F3>
Use the <ESC><0> key sequence for <F10>
Use the <ESC><!> key sequence for <F11>
Use the <ESC><@> key sequence for <F12>

Use the <ESC><Ctrl><M> key sequence for <Ctrl><M>
Use the <ESC><Ctrl><H> key sequence for <Ctrl><H>
Use the <ESC><Ctrl><I> key sequence for <Ctrl><I>
Use the <ESC><Ctrl><J> key sequence for <Ctrl><J>

Use the <ESC><X><X> key sequence for <Alt><x>, where x is any letter
key, and X is the upper case of that key

Use the <ESC><R><ESC><r><ESC><R> key sequence for <Ctrl><Alt><Del>
```

And powercycle the machine with:
```
racadm serveraction powercycle
```

See full options with eg:
```
> racadm help serveraction
serveraction -- perform system power management operations

Usage:

racadm serveraction <action>

action    server power management operation to peform

Valid actions:

powerdown       - power server off
powerup         - power server on
powercycle      - perform server power cycle
hardreset       - force hard server power reset
powerstatus     - display current power status of server
```

## Legacy - serial over LAN

We still have one old iDRAC which doesn't support SSH, in `backup-b32-1`. It can be accessed from the GW servers with `ipmitool`, and you can get a serial-over-lan console like:

```
ipmitool -I lan -H backup-b32-1-ipmi -U sown isol activate
```

To powercycle it:

```
ipmitool -I lan -H backup-b32-1-ipmi -U sown power off|on|cycle|reset|diag|soft
```

To get into the BIOS, <Esc><!> is the serial equivalent of <F11> and will get you a boot menu, then select system setup.