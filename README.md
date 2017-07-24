# Ubuntu-and-ROS-installation-in-beaglebone-green-wireless


1 Get the image.
  

wget https://rcn-ee.com/rootfs/2017-07-14/elinux/ubuntu-16.04.2-console-armhf-2017-07-14.tar.xz
  
2 Unpack and change directory
  tar xf ubuntu-16.04.2-console-armhf-2017-07-14.tar.xz
  cd ubuntu-16.04.2-console-armhf-2017-07-14
  
 3 Mount the sd card
 
 sudo ./setup_sdcard.sh --mmc /dev/mmcblk0 --dtb BeagleBone Green
 
 ----
 
 Create a Swap partition
 
 sudo mkdir -p /var/cache/swap/   
sudo dd if=/dev/zero of=/var/cache/swap/swapfile bs=1M count=1024
sudo chmod 0600 /var/cache/swap/swapfile 
sudo mkswap /var/cache/swap/swapfile 
sudo swapon /var/cache/swap/swapfile 

/var/cache/swap/swapfile    none    swap    sw    0   0

------
Wifi problem with commanctl 


-uninstall commanctl and connect with interface file

Note: If not connect your beagle bone create a manual ipv4 conexion in your pc.

Address 192.168.7.1
Netmask 30
Gateway 192.168.7.0

--------------

Ros installation 


1 sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

2 sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116

3 sudo apt-get update

4 sudo apt-get install ros-kinetic-ros-base

5 sudo rosdep init
rosdep update

6 source /opt/ros/kinetic/setup.bash



