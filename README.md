# CMPE283-ASSIGNMENT-1-Discovering VMX Features

Team members:
Tarun Pradeep Kasturi (015349685)
Harshit bhoraskar.    (015218606)

Q1:For each member in your team, provide 1 paragraph detailing what parts of the lab that member 
implemented / researched.

Tarun Pradeep Kasturi:
Created and setup the environment in Windows using Oracle VM and also the Linux Ubuntu
Build a kernal modules and established a copy of Linux Kernal
I've discussed with Harshit about the MSRs which is to be read in the SDM.
Modified some changes in the cmpe 283-1.c file by addiing logic funions for the output of various MSRs
Implemented and tested the output which we've got with the sample output shared in the canvas.

Harshit
Successfully build a environment in the windows using Oracle VM and downloaded the Linux ISO file.
The VM was allocated with 150GB storage space and 8Gb RAM.
Discussed the MSRs which were to be read in the SDM and successfully executed the code.
After inserting the module we've committed the cmpe283-1.c file and Makefile.
We've got the diff file after making changes in the repository

Q2:Describe in detail the steps you used to complete the assignment.

Firstly we need a machine capable to run Linux, VMX virtulization
To create a VM insall Oracle VM and Linux Ubuntu.
https://ubuntu.com/download/desktop
 
Now we ned to fork the Linux Repository:
https://github.com/torvalds/linux

Install the git:
sudo apt-get install git

Clone the kernal sources from the git repository:
git clone https://github.com/harshitbhoraskar/linux.git

Install the packages:
sudo apt-get install libncurses-dev gawk flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf

Copy the config file into the linux folder:
uname -a
cd linux
cp /boot/config-(linux kernal version) .config

Make the oldconfig file for building the kernal:
make oldconfig

Run the command to prepare to build the kernal:
make prepare

Install the required modules for the kernal:
make modules

Build the kernal using make command:
make

Copy the modules installed in the make modules step into the required folder:
sudo make INSTALL_MOD_STRIP=1 modules_install

Build the kernal
make istall

Reboot the Ubuntu system
sudo reboot

Create a new library cmpe283 
mkdir cmpe283

Go to the cmpe283 directory
cd cmpe283

Add the following command into the .c
MODULE_LICENCE("GPL_v2");

Use the make command to run makefile
make

Use the following commands to load and unload the kernal module
sudo insmod ./cmpe283-1.ko
sudo rmmod ./cmpe283-1.ko

We can verify the outout using the following command:
dmesg

