---
layout: post
date:  2020-07-28
title: Software Required For a Horn Telescope
summary:  Details of software installation required for a horn telescope
tags: ['School-Teachers', 'Students', 'Hobbyists' ]
categories: ['Horn Construction']
---

## Running the Spectrometer on a Computer with Ubuntu 20.04

Complete the following steps as needed:

#### A. How to Partition a Hard Drive for Ubuntu 20.04 Alongside Windows 10

   1. [Download Ubuntu Desktop 20.04 ISO onto hard drive in Windows.](http://releases.ubuntu.com/20.04/)

   2. Install a 32 GB or larger flash drive in the usb port.
      
   3. Download *BalenaEtcher* for Windows and install it if you don’t already have it.
   
   4. Run *BalenaEtcher*. Choose the Ubuntu20.04.iso file as the image and the flash drive as the target.

   5. Before installing Ubuntu on the Windows system, you need to partition the hard disk in Windows. 
      Open a Command Prompt window with admin rights:
         - In the Cortana search field, type in `Command Prompt`, or just CMD.
         - Right click the top result, and select `Run as Administrator`.
         - Click `Yes` on the popup to allow the app to make changes to your device.
         
   6. Enter the command `diskmgmt.msc` to open the Disk Management utility.

   7. Select the Windows partition, usually the C: volume, right-click on this partition and select the `Shrink Volume` option in order to reduce the partition size.

   8. Wait for the system to collect partition size data; then add the desired amount of space you want to shrink, and hit in the 'Shrink' button. The partition size to shrink by (which is the amount that will be allotted to Ubuntu) should be a minimum of 50 GB, and we recommend 100 GB or more, depending on the size of your hard drive.
      
   9. After the shrink process completes, a new unallocated space will be present in your drive. We’ll use this free space to install Ubuntu alongside Windows 10.

#### B. Install Ubuntu 20.04 Alongside with Windows

   1. Place the bootable flash drive in the USB port, and reboot the machine, holding down the bootable key (F12) in order to boot from the Ubuntu USB bootable image.

   2. On the first installation screen, select Install Ubuntu and hit Enter to start the installation process.

      This will complete the installation process, unless there is an error message indicating that device encryption (known as Bitlocker) may need to be turned off. If this is the case, complete the following:

      - Refer to the following webpage: [https://www.windowscentral.com/how-enable-device-encryption-windows-10-home](https://www.windowscentral.com/how-enable-device-encryption-windows-10-home)

      - Alternately, boot up in Windows. From the **Start** Menu, click the **Windows Administrative Tools**, then **Windows PowerShell** folder and tap **Windows PowerShell**.
      
        A command line window will open up. From the Powershell command line, type `Disable-BitLocker -MountPoint C:`

        Then reboot with the bootable flash drive in the USB port, and reboot the machine, holding down the bootable key (F12) in order to boot from the Ubuntu USB bootable image.

        On the first installation screen, select Install Ubuntu and hit Enter to start the installation process.


#### C. Install Gnuradio 

   1. Open a terminal window.
      
   2. Type `sudo apt install gnuradio`

#### D. Install gr-radio_astro 

   1. Open a terminal window.

   2. Install gnuradio external python dependencies and SDR drivers:
      `sudo apt install gnuradio gr-osmosdr airspy python3-h5py python3-ephem`

   3. Also install the following package: `sudo apt install git cmake liborc-0.4-dev`
      
   4. Clone the repository: From the terminal, type: `git clone https://github.com/WVURAIL/gr-radio_astro.git`

   5. Switch to the gr-radio_astro directory: `cd gr-radio_astro`

   6. Switch to the GNURadio 3.8 by typing: `git checkout gr38`

   7. Make a build directory: `mkdir build`, and then move to it: `cd build`  
      
   8. Then run the following in the build directory:

      ```
      cmake ..
      sudo make
      sudo make install
      ```
      
   9. Run the program in Gnuradio:
         - In a terminal window type `gnuradio-companion`
         - Open the *spectrometer_w_cal.grc* program as follows: 
            
           File --> Open --> gr-radio_astros --> examples --> *spectrometer_w_cal.grc*

#### E. How to Update files from the gr-radio_astro gr38 Repository

   1. Change to the *gr-radio_astro* folder on your computer.

   2. Type `git status`
      
   3. Check to see if you are in the gr38 branch. To change to gr38 branch, type `git checkout gr38`. Type `git status` to check. 

   4. Type `git pull`

   5. Run the program in Gnuradio:
      - In a terminal window type `gnuradio-companion`
      - Close the existing *spectrometer_w_cal.grc* program if it is in the program.
      - Open the new *spectrometer_w_cal.grc* program that is in the updated gr-radio_astro folder: 
            
         File --> Open --> gr-radio_astros --> examples --> *spectrometer_w_cal.grc*


##  Running the Spectrometer from a Flash Drive

   1. Write the image to a flash drive

   2. Run from the flash drive