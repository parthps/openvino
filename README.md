# openvino
This repository contains all the necessary files required to setup OpenVINO on Raspberry Pi 4.

Download and install Raspberry Pi imager from https://www.raspberrypi.com/software/

Select the OS as Raspberry Pi Legacy

Select the storage as your SD card.

Write the OS onto memory card.

After flashing remove the SD card and insert it again.

Goto the link https://www.raspberrypi.com/documentation/computers/configuration.html#setting-up-a-headless-raspberry-pi

Create 2 files on to the SD card a. Ssh with no extension b. wpa_supplicant.conf

Write this content in the wpa supplicant file ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev country=IN update_config=1

network={ ssid="" psk="" }

Write the name of your wifi with password

Remove the SD card and plug it into the Raspberry Pi and power on the pi

Wait for sometime to boot raspberry pi and connect to the wifi.

In your laptop install Putty https://www.putty.org/ and VNC https://www.realvnc.com/en/connect/download/viewer/

Open putty and in host name write raspberrypi.local

You will get the cmd access to the raspberry pi

Login : pi Pwd : raspberry

Run sudo raspi-config

Go to interface options and enable VNC

Then go to system options and then boot/auto login then click on desktop auto login

Click on finish and reboot the raspberry pi

Open vnc viewer

Connect to raspberrypi.local

Login as pi and password as raspberry

If can’t show display error occurs then go to putty again login as raspberry pi

Sudo raspi-config

Go to display options and change the resolution

Open browser in raspberry pi

Go to https://storage.openvinotoolkit.org/repositories/openvino/packages/2020.3/

Download the openvino toolkit l_openvino_toolkit_runtime_raspbian_p_2020.3.194

Go to https://docs.openvino.ai/latest/openvino_docs_install_guides_installing_openvino_raspbian.html#install-openvino

Follow the simple steps

sudo mkdir -p /opt/intel/openvino_2022

sudo tar -xf l_openvino_toolkit_runtime_raspbian_p_.tgz --strip 1 -C /opt/intel/openvino_2022

The OpenVINO environment variables are removed when you close the shell. As an option, you can permanently set the environment variables as follows: echo "source /opt/intel/openvino_2022/bin/setupvars.sh" >> ~/.bashrc

sudo usermod -a -G users "$(whoami)"

sh /opt/intel/openvino_2022/install_dependencies/install_NCS_udev_rules.sh

dmesg | grep Movidius

Face Detection using OpenVINO on R-PI Project 01: Face Detection

Clone the github repository into local system
git clone https://github.com/utkarsh270/openvino.git This repository contains both xml and bin file of Face Detection model. 2. Go to Face Detection folder

cd face-detect-ov-rpi /Face Detection Note: Add a single before and after Face Detection wording if not recognized 3. Run the python file (it should be python3)

python3 face_detection.py Method 2: If git clone isn’t working

Create a folder named face
mkdir face && cd face 2. Download xml and bin file using wget for Face Detection Retail from web browser and move it to face folder

Link : https://download.01.org/openvinotoolkit/2018_R4/open_model_zoo/face-detection-retail-0004/FP16/face-detection-retail-0004.xml

https://download.01.org/openvinotoolkit/2018_R4/open_model_zoo/face-detection-retail-0004/FP16/face-detection-retail-0004.bin

NOTE: Take only FP16 because VPU works only on FP16 . 3. Copy and paste the face_detection.py file in face folder of Raspberry Pi

Run python file using python3 command python3 face_detection.py Errors which might be faced:
cv2.error: OpenCV(4.4.0-openvino) ../opencv/modules/dnn/src/ie_ngraph.cpp:638: error: (-2:Unspecified error) Failed to initialize Inference Engine backend (device = MYRIAD): Can not init Myriad device: NC_ERROR in function 'initPlugin'
Either VPU isn’t working or you are using VPU in USB 3.0 ( Connect it to USB 2.0)

Next

Project 02: Face, Age & Gender Detection using OpenVINO & R-PI

Clone the github repository into local system
git clone https://github.com/ameer-aiml/age-gender-openvino-rpi 2. Go to Age Gender Detection folder

cd age-gender-openvino-rpi/AgeGender This repository contains 3 different models. One for Face Detection, another for Age and last one for Gender Detection. Both the files of Face Detection is available. The .caffemodel files of Age and Gender are missing. 3. Download the Age and Gender Caffe model from this site using the command wget

(Github doesn’t support more than 25 mb file) wget https://www.dropbox.com/s/iyv483wz7ztr9gh/gender_net.caffemodel wget https://www.dropbox.com/s/xfb20y596869vbb/age_net.caffemodel 4. Run the python file (it should be python3)

python3 face_detection.py
