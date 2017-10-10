# Alienware13R3_Linux_Darknet
This steps will allow you to: 
* Use only Nvidia Graphic Card
* Install Cuda9
* Install Opencv3.3.0
* Use Darknet examples

-----------------------------------------------------------------------
### 1rs 
#### Prepare your Laptop for a dual boot: 
##### Ref: https://github.com/andrewwakeling/alienware-13-r3-ubuntu-16.04
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

Creating a bootable USB Ubuntu installer can be done using Rufus... 

----------------------------------------------------------------------

### 2nd

#### Download and Proceed to install Ubuntu 16.04.3

 - Do not add 3rth Libraries
 - Once is installed-> using Alternatives Drivers -> set Nvidia and Apply Changes
 - Restart and Check that option keeps selected. ( if yes -> Nvidia is working) 

## Steps CUDA:
-> https://pjreddie.com/darknet/install/#cuda
Main Downdload ( Deb Local ) from --> https://developer.nvidia.com/cuda-downloads
Main Steps from http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html are: 

    * `sudo dpkg -i cuda-repo-ubuntu1604-9-0-local_9.0.176-1_amd64.deb`
    * `sudo apt-key add /var/cuda-repo-<version>/7fa2af80.pub`
    * `sudo apt-get update`
    * `sudo apt-get install cuda`
Then add fresh intalled Cuda9.0 folder (/usr/local/cuda-9.0/bin) to PATH environtment, ref --> http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html ( 7.1.1. Environment Setup )

To add this path to the PATH variable:

    $ export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}

In addition, when using the runfile installation method, the LD_LIBRARY_PATH variable needs to contain /usr/local/cuda-9.0/lib64 on a 64-bit system:

    To change the environment variables for 64-bit operating systems:
    $ export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64\
                             ${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

Read more at: http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#ixzz4v3XBIfiC
Follow us: @GPUComputing on Twitter | NVIDIA on Facebook


## To install Opencv: 
-> http://docs.opencv.org/trunk/d7/d9f/tutorial_linux_install.html (Cloning the GIT Version)

#### Remember to do the Final step https://pjreddie.com/darknet/install/#cuda : 

* At darknet (Makefile), change the 2nd line of the Makefile to read:
OPENCV=1

* Re-make the project. Then use the imtest routine to test image loading and displaying:
./darknet imtest data/eagle.jpg

or

./darknet detector demo cfg/coco.data cfg/yolo.cfg yolo.weights <video file>

Download proper weights from YOLO --> https://pjreddie.com/darknet/yolo/

---------------------------------------------------------------------------------------

Results: 

With a grayscale video 640x480: 

* YOLOv2_608x608.weights --> 10-12 Fps
./darknet detector demo cfg/coco.data cfg/yolo.cfg YOLOv2_608x608_COCO_trainval.weights VideoTestTrackingPeople.mov

* YOLOv2_VOC2007+2012.weights --> 28 Fps
 ./darknet detector demo cfg/voc.data cfg/yolo-voc.cfg YOLOv2_VOC2007+2012.weights VideoTestTrackingPeople.mov




