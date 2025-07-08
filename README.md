#  Multistectral camere with filtre wheel (MSX)

It is a freeware software for non commercial use for operating multispectral imagind in VISIBLE, NEAR INFRARED AND LONG WAVE INFRARED throgth use of Monochromatic, RGB and thermal sensors. 

The monitoring of the temperature distribution is important for various reasons: inspection, defect analysis, quality control, rescue, etc. for various fields from industrial, construction, bio-medical, emergency relief to cultural heritage.

This repository allow you to build and controll a low cost prototype of this instrument.




### Update and Upgrade, open terminal and run the following command
```
sudo apt update 

sudo apt upgrade
```

### Raspberry QH IMX477 CSI camera Set-up
- Download the installation package from:
```
wget https://github.com/ArduCAM/MIPI_Camera/releases/download/v0.0.3/install_full.sh

chmod +x install_full.sh

./install_full.sh -m imx477
```
- Test and open a window with video stream from Raspberry QH camera
```
v4l2-ctl --list-devices

v4l2-ctl --list-formats-ext -d /dev/video0
```


### Seek Thermal Set-up
- Download and unzip the Seek Thermal SDK v4.x 
```
https://developer.thermal.com/support/solutions/articles/48001240854-seek-thermal-sdk-v4-3
```
#### Open a command line, navigate inside the unzipped Seek_Thermal_SDK_4.x.x.x folder and install the .deb by using the command line and OS package manager.

- For **Raspberry**
```
sudo apt-get install ./seekthermal-sdk-dev-4.x.x.x_armhf.deb 
```

- For Linux OS
```
sudo dpkg --install ./seekthermal-sdk-dev-4.x.x.x_arm64.deb  
```

- Reboot or reload the udev rules.
```
sudo udevadm control --reload
```
- Plug in the OEM Starter Kit and run the seekcamera-sdl example to start imaging.
``` 
seekcamera-sdl
```

### Basler Camera Set-up
- Download the official installation package from:

https://en.ids-imaging.com/files/downloads/ids-software-suite/readme/readme-ids-software-suite-linux-4.95.1_EN.html


```
sudo dpkg --install ./ids-peak-with-ueyetl-linux-arm64-x.x.x.x # Linux OS

sudo dpkg -i ids-peak-linux-x86-2.4.0.0-64.deb

chmod u+x ueyesdk-setup-4.20-usb-amd64.gz.run 
./ueyesdk-setup-4.20-usb-amd64.gz.run 


pip3 install pypylon    

python3 -m pip3 install pypylon
```



### Install Arduino IDE on Jetson Dev Kit
```
git clone https://github.com/JetsonHacksNano/installArduinoIDE

cd installArduinoIDE

./installArduinoIDE.sh
```





##  MSXSoftware
This software allows you controlling the acquisition of multispectral images in severeal wavelength bands Vis-NIR and LWIR

Thermal frames can be management in Temperature (°C) or in radiometric format RAW type.
Also can perform a conversion of RAW data into temperature values from the input parameters on object surface emissivity and environment.

An image of the GUI is represented in 'MSXSoftware.png' folder.

##  RUN MSXSoftware
Before launching it, check that the execute permission is granted to the user, if not run in terminal 
```
chmod u+x MSXSoftware
```

To start the program you can double-click on the MSXSoftware icon or use the following terminal command:
```
./MSXSoftware
```

### Acquired DATA with MSX Camera
For each sample the MSX camera can acquired a stack of 13 images in following wavelength spectral badds:
- BN470
- BN532
- BN595
- BN630
- BN660
- Bi685
- BN740
- BN785
- BN810
- BN850
- BN940
- RGB
- Thermla (LWIR) 

**Environmental sensors data** like: 
- Temperature (°C) 
- Relative humidity (\%) 
- Dioxide of carbon (ppm)
- Light intensity (lux) 

All this data are stored in one CSV format file, named ```ENV_Data_DD_MM_YYYY.csv``` followed by the date. 

For each measurment of environmental data are sotred in new row of file and also is added a time of acquisition.
















