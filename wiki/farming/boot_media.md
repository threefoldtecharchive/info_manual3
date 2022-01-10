## Generating boot media

A computer becomes a 3Node when it boots Zero OS by downloading it over a network connection. For most farmers, this means copying a "bootstrap" file onto a USB flash drive. When the computer is instructed to boot from the USB stick, it bootstraps the system into a state where it can download and start the operating system.

> __IMPORTANT:__ Disks won't be accepted as storage devices unless they're completely empty. 
>Please ensure that all disks are wiped before booting the nodes. 
Also when moving nodes from TFGrid2 to TFGrid3, this step is absolutely necessary.
>
> A way to do it: 
> - Boot an arch linux from an USB stick and execute `wipefs -a -f /dev/sda/$YOURSSD`.

### Bootstrap

Proceed to the [bootstrap site](http://v3.bootstrap.grid.tf) to generate your boot media. Enter your farm id and select the same network that your farm is registered on (note that mainnet is called "Production" here).

#### EFI image and kernel

If your systems supports it, EFI is recommended over legacy booting. The "EFI IMG" option will generate an image file that can be flashed to a USB stick. On Unix based systems, this can be done with `dd` on the command line. A cross platform and open source tool called [balenaEtcher](https://www.balena.io/etcher/) has also been recommended by the community for this purpose.

Alternatively, you can download the EFI kernel using the "EFI FILE" option. Format the USB stick to FAT and follow the given instructions for the file name and directory structure. This can be handy if you just want to replace the boot file on an existing boot USB or generate a new USB on Windows without installing addtional software.

Next, [boot your node](@booting_node).