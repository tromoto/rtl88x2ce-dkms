## RTL88x2CE dkms module driver
tested on AUSUS TUF A15 series 506 xx
Ubuntu 20.04.4
Kernel 5.13.0-41-generic #46~20.04.1-Ubuntu SMP Wed Apr 20 13:16:21 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux  (and earlier versions as well)


### DKMS
This driver can be installed using [DKMS]. This is a system which will automatically recompile and install a kernel module when a new kernel gets installed or updated. To make use of DKMS, install the `dkms` package, which on Debian (based) systems is done like this:
```
$ sudo apt-get install dkms
```

### Installation of Driver
In order to install the driver open a terminal in the directory with the source code and execute the following command:
```
$ sudo make dkms_install
```

### Removal of Driver
In order to remove the driver from your system open a terminal in the directory with the source code and execute the following command:
```
$ sudo make dkms_remove
```

### Make
For building & installing the driver with 'make' use
```
$ make && make install
```



### Manual Install
```
git clone https://github.com/tromoto/rtl88x2ce-dkms.git
sudo cp rtl88x2ce-dkms/rtw88_blacklist.conf /etc/modprobe.d/rtw88_blacklist.conf
sudo mkdir /usr/src/rtl88x2ce-35403
sudo cp -Rv rtl88x2ce-dkms/* /usr/src/rtl88x2ce-35403/
sudo dkms add -m rtl88x2ce -v 35403
sudo dkms build -m rtl88x2ce -v 35403
sudo dkms install -m rtl88x2ce -v 35403
```

**After installing the driver:** 
```
echo "options rtw88_pci disable_aspm=1" | sudo tee  /etc/modprobe.d/rtw88_pci.conf
```
*NOTE:* 
The above should work ok with native ubuntu 20.04.x kernel and driver, i.e. no need to install this driver.

*NOTE2:* 
Additionally one could try to change in  /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
line:
wifi.powersave = 3
to 
wifi.powersave = 2 




## Install the module

`sudo modprobe rtl88x2ce`


