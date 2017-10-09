# Alienware13R3_Linux_Darknet
This steps will allow you to: 
* Use only Nvidia Graphic Card
* Install Cuda9
* Install Opencv3.3.0
* Use Darknet examples

-----------------------------------------------------------------------
### 1rs Prepare your Laptop Allows to Install Linux: Follow Main Steps here: 

Preparation
BIOS

Turn off Secure Boot in the BIOS. This will make it easier to install several 3rd party drivers.

I recommend leaving UEFI on. Be aware that to get entries in your bios, you will need to manually add a new entry and select the appropriate *.efi file.

I believe that you need to switch the SATA interface from RAID to AHCI before you're able to install Ubuntu. (I couldn't get the Ubuntu installer to detect the drive when using RAID but maybe this could be resolved with extra drivers).

WARNING: If Windows was installed with RAID, switching the SATA interface to AHCI will cause Windows to BSOD.

Be very wary of some guides that give instruction on to continue using Windows even after switching to ACHI. You can very easily stop Windows booting properly. Even with recovery points, don't expect this to be easy to undo. I highly recommend that you backup any important data.

trunet has advised me that this solution works.
Dual-boot with Windows

It is recommended that you have Windows 10 installed first. If you need to reinstall, you shouldn't need a product key as it should be embedded in the BIOS. If necessary, shrink the partition to make room for Ubuntu.

Installing Windows 10 is easy. Simply create a bootable USB using the Windows 10 Media Creation Tool. Get the drivers from Dell's website and get it all working.
Ubuntu installer

Creating a bootable USB Ubuntu installer can be done using Rufus, using these instructions.

----------------------------------------------------------------------

### 2nd

#### Download and Proceed to install Ubuntu 16.04.3

 - Do not add 3rth Libraries
 - Once is installed-> using Alternatives Drivers -> set Nvidia and Apply Changes
 - Restart and Check that option keeps selected. ( if yes -> Nvidia is working) 

## Steps CUDA:
-> https://pjreddie.com/darknet/install/#cuda
Main Downdload ( Deb Local ) from --> https://developer.nvidia.com/cuda-downloads

## To install Opencv: 
-> http://docs.opencv.org/trunk/d7/d9f/tutorial_linux_install.html (Cloning the GIT Version)

#### Finally follow next steps from Darknet Tutorial for Opencv https://pjreddie.com/darknet/install/#cuda : 

* Next, change the 2nd line of the Makefile to read:
OPENCV=1

* You're done! To try it out, first re-make the project. Then use the imtest routine to test image loading and displaying:
./darknet imtest data/eagle.jpg


