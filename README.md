# RPI3-NCS

### Intel® Neural Compute Stick - ![[Get Started]](https://software.intel.com/en-us/movidius-ncs-get-started)


# Get Started 
### Step 1: Gather Your Equipment

__Before you start, make sure you have the following:__
* Ubuntu* 16.04 operating system, RPI3 Model B or Ubuntu VirtualBox instance
* Intel® Movidius™ Neural Compute Stick
* Internet connection to download and install the Intel® Movidius™ Software Development Kit (SDK)
 

### Step 2: Install the SDK

__To install, run these commands in a terminal window:__
    
    mkdir -p ~/workspace 
    cd ~/workspace
    git clone https://github.com/movidius/ncsdk.git
    cd ncsdk
    make install
    
 
### Step 3: Test the Installation

__Run the built-in examples to test your installation. To do this, plug the compute stick into the USB port, and then run the following commands in a new terminal window:__
	  
    cd ~/workspace/ncsdk
    make examples

# How to run tensorflow and opencv
#### get shell script to install package - ![[install.sh]](https://github.com/yehengchen/RPI-NCS/blob/master/install.sh)
	
	$ chmod 777 ./install.sh
	$ ./install.sh
	...
	$ python3
	>>> import cv2
	>>> import tensorflow
