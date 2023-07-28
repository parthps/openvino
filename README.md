1.	# openvino
2.	This repository contains all the necessary files required to setup OpenVINO on Raspberry Pi 4.

3.	Download and install Raspberry Pi imager from https://www.raspberrypi.com/software/

4.	Select the OS as Raspberry Pi Legacy

5.	Select the storage as your SD card.

6.	Write the OS onto memory card.

7.	After flashing remove the SD card and insert it again.

8.	Goto the link https://www.raspberrypi.com/documentation/computers/configuration.html#setting-up-a-headless-raspberry-pi

9.	Create 2 files on to the SD card a. Ssh with no extension b. wpa_supplicant.conf

10.	Write this content in the wpa supplicant file ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev country=IN update_config=1

11.	network={ ssid="" psk="" }

12.	Write the name of your wifi with password

13.	Remove the SD card and plug it into the Raspberry Pi and power on the pi

14.	Wait for sometime to boot raspberry pi and connect to the wifi.

15.	In your laptop install Putty https://www.putty.org/ and VNC https://www.realvnc.com/en/connect/download/viewer/

16.	Open putty and in host name write raspberrypi.local

17.	You will get the cmd access to the raspberry pi

18.	Login : pi Pwd : raspberry

19.	Run sudo raspi-config

20.	Go to interface options and enable VNC

21.	Then go to system options and then boot/auto login then click on desktop auto login

22.	Click on finish and reboot the raspberry pi

23.	Open vnc viewer

24.	Connect to raspberrypi.local

25.	Login as pi and password as raspberry

26.	If can’t show display error occurs then go to putty again login as raspberry pi

27.	Sudo raspi-config

28.	Go to display options and change the resolution

29.	Open browser in raspberry pi

30.	Go to https://storage.openvinotoolkit.org/repositories/openvino/packages/2020.3/

31.	Download the openvino toolkit l_openvino_toolkit_runtime_raspbian_p_2020.3.194

32.	Go to https://docs.openvino.ai/latest/openvino_docs_install_guides_installing_openvino_raspbian.html#install-openvino

33.	Follow the simple steps

34.	sudo mkdir -p /opt/intel/openvino_2022

35.	sudo tar -xf l_openvino_toolkit_runtime_raspbian_p_.tgz --strip 1 -C /opt/intel/openvino_2022

36.	The OpenVINO environment variables are removed when you close the shell. As an option, you can permanently set the environment variables as follows: echo "source /opt/intel/openvino_2022/bin/setupvars.sh" >> ~/.bashrc

37.	sudo usermod -a -G users "$(whoami)"

38.	sh /opt/intel/openvino_2022/install_dependencies/install_NCS_udev_rules.sh

39.	dmesg | grep Movidius

40.	Face Detection using OpenVINO on R-PI Project 01: Face Detection

41.	Clone the github repository into local system
42.	git clone https://github.com/utkarsh270/openvino.git This repository contains both xml and bin file of Face Detection model. 2. Go to Face Detection folder

43.	cd face-detect-ov-rpi /Face Detection Note: Add a single before and after Face Detection wording if not recognized 3. Run the python file (it should be python3)

44.	python3 face_detection.py Method 2: If git clone isn’t working

45.	Create a folder named face
46.	mkdir face && cd face 2. Download xml and bin file using wget for Face Detection Retail from web browser and move it to face folder

47.	Link : https://download.01.org/openvinotoolkit/2018_R4/open_model_zoo/face-detection-retail-0004/FP16/face-detection-retail-0004.xml

48.	https://download.01.org/openvinotoolkit/2018_R4/open_model_zoo/face-detection-retail-0004/FP16/face-detection-retail-0004.bin

49.	NOTE: Take only FP16 because VPU works only on FP16 . 3. Copy and paste the face_detection.py file in face folder of Raspberry Pi

50.	Run python file using python3 command python3 face_detection.py Errors which might be faced:
51.	cv2.error: OpenCV(4.4.0-openvino) ../opencv/modules/dnn/src/ie_ngraph.cpp:638: error: (-2:Unspecified error) Failed to initialize Inference Engine backend (device = MYRIAD): Can not init Myriad device: NC_ERROR in function 'initPlugin'
52.	Either VPU isn’t working or you are using VPU in USB 3.0 ( Connect it to USB 2.0)

53.	Next

54.	Project 02: Face, Age & Gender Detection using OpenVINO & R-PI

55.	Clone the github repository into local system
56.	git clone https://github.com/ameer-aiml/age-gender-openvino-rpi 2. Go to Age Gender Detection folder

57.	cd age-gender-openvino-rpi/AgeGender This repository contains 3 different models. One for Face Detection, another for Age and last one for Gender Detection. Both the files of Face Detection is available. The .caffemodel files of Age and Gender are missing. 3. Download the Age and Gender Caffe model from this site using the command wget

58.	(Github doesn’t support more than 25 mb file) wget https://www.dropbox.com/s/iyv483wz7ztr9gh/gender_net.caffemodel wget https://www.dropbox.com/s/xfb20y596869vbb/age_net.caffemodel 4. Run the python file (it should be python3)

59.	python3 face_detection.py
