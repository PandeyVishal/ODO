ODO - The AI chatbot

This is a completely offline chatbot suitable for theatres.\
It is still in development, so you might see few changes related to Dialogue System and some files moving around.
The chatbot has been modelled to represent the character of Little Prince from the book "The Little Prince". You can change the character of the chatbot by modifying file models/dialogue_system/dialogue_system.py. For more information on the project, please refer the [publication](https://github.com/ravibhushan0487/ODO/blob/master/The%20ODO%20Project.pdf)

This chatbot is suitable for Linux environment. It is compatible to Nvidia Jetson Nano. For setup information please read on.
 

 
Setup for Linux Environment(Ubuntu 18.0.4):

1. Install anaconda following this link: \
https://www.digitalocean.com/community/tutorials/how-to-install-anaconda-on-ubuntu-18-04-quickstart

2. In the terminal, type the following commands:\
$ conda create --name chatbot python=3\
$ conda activate chatbot\
$ conda install -c conda-forge keras\
$ conda install -c anaconda pandas\
$ conda install -c anaconda scikit-learn\
$ conda install -c conda-forge tensorflow-hub\
$ conda install -c conda-forge opencv=4.1.0

3. Before starting the chatbot, you will have to build models for dialogue_system and poem_generator. Follow the ReadMe.md file of models/dialogue_system and models/poem_generator to train and generate the models.

3. Execute the below command to start the chatbot:\
$ conda activate chatbot\
$ python3 odo.py

Setup for Nividia Jetson Nano:

1. In the terminal, execute the following commands:\
$ sudo fallocate -l 8G /swapfile\
$ sudo chmod 600 /swapfile\
$ sudo mkswap /swapfile\
$ sudo swapon /swapfile\
$ swapon --show\
$ echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab\
$ sudo apt-get install libhdf5-serial-dev hdf5-tools libhdf5-dev\
$ sudo apt-get install libblas-dev liblapack-dev libatlas-base-dev gfortran\
$ sudo apt-get install python3-pip\
$ sudo pip3 install Cython\
$ sudo apt-get install python3-numpy\
$ sudo pip3 install pybind11\
$ sudo pip3 install scipy\
$ sudo pip3 install keras\
$ wget https://developer.download.nvidia.com/compute/redist/jp/v42/tensorflow-gpu/tensorflow_gpu-1.15.0+nv19.11-cp36-cp36m-linux_aarch64.whl
\
$ sudo pip3 install tensorflow_gpu-1.15.0+nv19.11-cp36-cp36m-linux_aarch64.whl\
$ sudo pip3 install pandas\
$ sudo pip3 install --upgrade Cython\
$ sudo pip3 install scikit-learn\
$ sudo pip3 install tensorflow-hub

2. If you have done a ssh to Jetson Nano and no display is attached to it, then please execute the below command:\
$ export DISPLAY=:0

3. Execute the below command to start the chatbot:\
$ python3 odo.py

What to expect:\
If you are using a laptop, then your webcam will start and it will try to detect a face. Only after face is detected will the chatbot start. If you are using Jetson, then this will activate the USB camera connected to jetson and wait till it detects the face.

Work In Progress:\
1. We are reconfiguring the character of chatbot by adding/removing new stories.
2. Integrating two or more cameras to capture user emotions.
2. This chatbot will get divided into three Jetson Nanos. First jetson will have the chatbot dialogue system and the poem generator. Second and third chatbot will have two USB cameras attached to them and will only do emotion detection. These two emotion detecting jetsons will communicate over lan via UDP protocol with the chatbot jetson.

