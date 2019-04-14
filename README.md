# RPI3-NCS

#### Intel® Neural Compute Stick - [[Get Started]](https://software.intel.com/en-us/movidius-ncs-get-started)
#### Intel® Movidius™ Neural Network Community - [[New Discussion]](https://ncsforum.movidius.com/)

# Get Started 
### Step 1: Gather Your Equipment

__Before you start, make sure you have the following:__
* Ubuntu* 16.04 operating system, RPI3 Model B or Ubuntu VirtualBox instance
* Intel® Movidius™ Neural Compute Stick
* Internet connection to download and install the Intel® Movidius™ Software Development Kit (SDK)
 

### Step 2: Install the SDK - (Pick one Version)

__To install NCSDK 1, run these commands in a terminal window:__
    
    mkdir -p ~/workspace 
    cd ~/workspace
    git clone https://github.com/movidius/ncsdk.git
    cd ncsdk
    make install

__To install NCSDK 2.x you can use the following command to clone the ncsdk2__
	
	mkdir -p ~/workspace
	cd ~/workspace
	git clone -b ncsdk2 https://github.com/movidius/ncsdk.git
    cd ncsdk
    make install

#### if you've installed tensorflow - “INSTALL_TENSORFLOW=no”
	
	gedit ncsdk/ncsdk.conf 
	...
	MAKE_PROCS=1
	SETUPDIR=/opt/movidius
	VERBOSE=yes
	SYSTEM_INSTALL=yes
	CAFFE_FLAVOR=ssd
	CAFFE_USE_CUDA=no	
	INSTALL_TENSORFLOW=no
	INSTALL_TOOLKIT=yes

### Step 3: Test the Installation

__Run the built-in examples to test your installation. To do this, plug the compute stick into the USB port, and then run the following commands in a new terminal window:__
	  
    cd ~/workspace/ncsdk/examples/apps/hello_ncs_py
	make run
	...
	making run
	python3 hello_ncs.py;
	Hello NCS! Device opened normally.
	Goodbye NCS! Device closed normally.
	NCS device working.
	
	cd ~/workspace/ncsdk
	make examples

# How to run tensorflow and opencv
#### get shell script to install package - [[install.sh]](https://github.com/yehengchen/RPI-NCS/blob/master/install.sh)[[Tensorflow - 1.8.0]](https://github.com/lhelontra/tensorflow-on-arm/releases)
	
	$ chmod 777 ./install.sh
	$ ./install.sh
	...
	$ python3
	>>> import cv2
	>>> import tensorflow
	
# NCAPPZOO Examples
#### The ncappzoo is a valuable resource for NCS users and includes community developed applications and neural networks for the NCS - [[ncappzoo]](https://github.com/movidius/ncappzoo)

	git clone https://github.com/movidius/ncappzoo.git


#### NC App Zoo Repository Layout
See the README file in each of these directory or just click on the links below to explore the contents of the NC App Zoo.

* [apps](https://github.com/movidius/ncappzoo/blob/master/apps/README.md) : Applications built to use the Intel Movidius NCS. This is a great place to start in the NC App Zoo!
* [caffe](https://github.com/movidius/ncappzoo/blob/master/caffe/README.md) : Scripts to download caffe models and compile graphs for use with the NCS
* [tensorflow](https://github.com/movidius/ncappzoo/blob/master/tensorflow/README.md) : Scripts to download TensorFlow™ models and compile graphs for use with the NCS
* data : Data and scripts to download data for use with models and applications that use the NCS

### Makefile Guidance - [[MAKEFILE_GUIDANCE]](https://github.com/movidius/ncappzoo/blob/master/MAKEFILE_GUIDANCE.md)
#### Makefile required targets for ncappzoo/apps directory:

    [make help] : Display make targets and descriptions.
    [make data] : Download data (images, etc.) If no data download required create empty target.
    [make deps] : Download/Prepare/compile networks. If not needed create empty target.
    [make all] : Prepares everything needed to run the application including other projects in the repository. Should not run application, should not popup GUI.
    [make run] : Runs the application with default parameters if needed.
    [make clean] : Removes all the files in this project directory that may get created when making or running this project. Should not clean other projects in the repository.

#### Makefile required targets for ncappzoo/caffe and ncappzoo/tensorflow directories:

    [make help] : Display make targets and descriptions.
    [make all] : creates a graph file for the network and does one of compile, check, or profile on it. Should not bring up GUI, or run lengthy program.
    [make deps] : Download/Prepare networks. If not needed create empty target
    [make compile] : Run the NCSDK compiler to create a graph file.
    [make profile] : Run the NCSDK profiler to display a profile of the network
    [make check] : Run the NCSDK checker to validate the network
    [make run] : Run a simple program demonstrating use of the compiled network
    [make clean] : Removes all the files in this project directory that may get created when making or running this project. Should not clean other projects in the repository.

### Contributing to the Neural Compute App Zoo (NC App Zoo) - [[CONTRIBUTING]](https://github.com/movidius/ncappzoo/blob/master/CONTRIBUTING.md)
