# sakis3g-for-3G-modems
**```sakis3g```** is a script which creates an Internet connection using 3G modems. The software works with most USB and Bluetooth modems. ```sakis3g``` is frequently used in devices such as Raspberry Pi and BeagleBone Black. 

There are situations where some USB 3g modems are not detected by the default modem manager softwares or establishing the connection fails frequently. ```sakis3g``` can be helpful in solving these problems.

###Installing sakis3g

You can install sakis3g simply by downloading the [**```sakis3g```**](https://github.com/Pahan-Madusha/sakis3g-for-3G-modems/blob/master/sakis3g?raw=true) file from this repository, copying it to ```/usr/local/bin``` directory and making it executable. 

```sudo cp /path/to/downloaded/directory/sakis3g /usr/local/bin/sakis3g ``` <br>
```sudo chmod +x /usr/local/bin/sakis3g```<br>

Click [here](http://www.sakis3g.com/downloads/sakis3g.tar.gz) to download the latest version of ```sakis3g```

###Using sakis3g

```sakis3g``` has an interractive mode which provides a nice GUI for the user. It can be launched as follows. 

```./sakis3g --interactive```<br>

Select or enter the relavant options such as APN, User Name and etc to connect. 

If you plan to connect to internet regularly through ```sakis3g```, using the interractive mode may be tiring. You can simply write a script for your modem and run it once to connect to the internet. You can even make this script run automatically when your modem is plugged in, which makes you do nothing to connect to the internet.  

###Using ```NET_CONNECT```

[**```NET_CONNECT```**](https://github.com/Pahan-Madusha/sakis3g-for-3G-modems/blob/master/NET_CONNECT) file provides a simple script which can be run to connect to the internet. But the ```NET_CONNECT``` file needs to be changed according to your modem and sudo password.

* Replace every **```<password>```** with your root password. 
* **```<vendorID:productID>```** must be replaced according to your modem. 
  * Make sure you've plugged in your 3g modem
  * Fireup a shell and do a ```lsusb```
  * You will get some devices plugged in to your PC including the 3g modem
  * Look for your 3g modem and get the vendorId and productId. 
  * eg: For ```Bus 003 Device 013: ID 19d2:0151 ZTE WCDMA Technologies MSM``` <br>
    **```vendorId = 19d2```**  and **```productId = 0151```**
* Replace **```<APN>```** by the APN of your network provider

If you have ```modemmanager``` installed, it won't allow ```sakis3g``` to use the modem. 
The lines 
```mmcli --modem=/org/freedesktop/ModemManager1/Modem/x -d``` in the ```NET_CONNECT``` script solves this by disabling the modem manager. 
   
###Connect to internet automatically when 3g modem is plugged in

Please follow [this](http://askubuntu.com/questions/284224/autorun-a-script-after-i-plugged-or-unplugged-a-usb-device) guide and run the cutomarized ```NET_CONNECT``` script as the script in above guide.  

