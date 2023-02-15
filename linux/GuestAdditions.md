# How to install VirtualBox Guest Additions on Ubuntu
>This tutorial was tested on Lubuntu 22.04.1 [Reference.](https://linuxize.com/post/how-to-install-virtualbox-guest-additions-in-ubuntu/) (13 / February / 2022)

1. Once you have started your VM, open a terminal as a sudo user and run the following commands:
    ```
    $ sudo apt update
    $ sudo apt install build-essential dkms linux-headers-$(uname -r)
    ```
    Where (uname -r) prints the running Kernel Version

2. From the virtual machine menu, click `Devices -> Insert Guest Additions CD Image`

    a. If you come accross an error message saying that your system doesn't have a CD-ROM, stop the virtual machine, open your VM settings an on the 'Storage' tab add a new CD-ROM (Optical device). 

3. On your terminal, create a new directory, we will use this as the mount point for our ISO file:
    ``` 
    $ sudo mkdir -p /mnt/cdrom
    $ sudo mount /dev/cdrom /mnt/cdrom
    ```
4. Navigate to the new directory and run the `VboxLinuxAdditions.run` script to install the guest additions:
    ```
    $ cd /mnt/cdrom
    $ sudo sh ./VBoxLinuxAddition.run --nox11
    ```
    The `--nox11` option will tell the installer not to open a new xterm window.
    The output should look like below:
    ```
    Verifying archive integrity... All good.
    Uncompressing VirtualBox 5.2.32 Guest Additions for Linux........
    ...
    VirtualBox Guest Additions: Starting.
    ```
5. Once this process is finished, your VM display should automatically resize to fit your window size, if not, a reboot is recommended
    ```
    $ sudo shutdown -r now
    ```
    or 
    ```
    $ sudo reboot
    ```