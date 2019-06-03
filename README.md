# Lenovo-ideapad-330-ARR-issues

The repository is expected to help people with Lenovo IdeaPad 330 notebook having issues with Ubuntu operating system and its derivatives with the probable fixes that will enhance the experience



## Issue-1: None of the ubuntu distros are getting installed

**Solution**: Ubuntu distros lower than `18.10` will not work in this laptop, as minimum kernal version required is `4.18`.

So install ubuntu 18.10 / xubuntu 18.10 / lubuntu 18.10 / kubuntu 18.10 in `UEFI` mode

## Issue-2: Wifi is not working

**Solution**: Install drivers seperatly. In most of the cases the wifi network card manufacturer is `Elan tech` for this model.

So just run the following commands to download and install
```
git clone https://github.com/tomaspinho/rtl8821ce.git
cd rtl8821ce/
sudo make all
sudo make install
sudo modprobe -a 8821ce
```
#### Check your wifi networks!

## Issue-3: Touchpad is not working at all

**Solution**: You need to upgrade kernel to minimum `4.19.15-041915-generic
`. From this kernal version, the touchpad drivers are present in the kernal.

So just download the kernal files and upgrade.
Visit https://kernel.ubuntu.com/~kernel-ppa/mainline/ to choose a kernal version

If you want to download `4.19.15`, try the steps

#### First download the files
```
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.15/linux-headers-4.19.15-041915_4.19.15-041915.201901130432_all.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.15/linux-headers-4.19.15-041915-generic_4.19.15-041915.201901130432_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.15/linux-modules-4.19.15-041915-generic_4.19.15-041915.201901130432_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.15/linux-image-unsigned-4.19.15-041915-generic_4.19.15-041915.201901130432_amd64.deb
```
#### Install
```
dpkg -i linux-headers-4.19.15-041915_4.19.15-041915.201901130432_all.deb
dpkg -i linux-headers-4.19.15-041915-generic_4.19.15-041915.201901130432_amd64.deb
dpkg -i linux-modules-4.19.15-041915-generic_4.19.15-041915.201901130432_amd64.deb
dpkg -i linux-image-unsigned-4.19.15-041915-generic_4.19.15-041915.201901130432_amd64.deb
```
#### Reboot


## Issue-3: Random freezes during normal usage
There is a common issue for all the AMD ryzen processors of freezing during the normal usage which is due to the current incompatibility of the Linux Kernel which is partially implemented as of now and it is better to disable the C6 state in order to have a better and stable system performance.

The issue is reported at - https://bugzilla.kernel.org/show_bug.cgi?id=196683

Thanks to Jeff Fredrickson jfredrickson(https://github.com/jfredrickson/disable-c6) for the fix.

**Solution**:The script actually needs the msr  kernel module to be enabled  to be able to perform so for it to happen we have to follow the step below-

### Loading msr

Open the terminal and the file manager using the Sudo command 
.
This will give us the super user access to the file manager

 Go to /etc/modules-load.d/

Create a file msr.conf

Open the file and write just msr and save it .

### Installation of disable C6 script:

```
git clone https://github.com/jfredrickson/disable-c6.git
cd disable-c6
git submodule init
git submodule update
sudo ./install.sh
```

### Reboot


Thanks to Debjyoti Saha(https://github.com/debojyoti) for his original contributions





