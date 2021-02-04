# OpenCV-Playing-Card-Detector

This is a Python program that uses OpenCV to detect and identify playing cards from a PiCamera / USB Camera video feed on a Raspberry Pi model 3 or newer.

### Pre-Req / Dependencies
Open your terminal / ssh into Raspberry Pi and install the following python packages that we will need. Note that OpenCV installation can take a while as it's a big package.

```
sudo apt-get install python-picamera python3-picamera libatlas-base-dev libhdf5-dev libhdf5-serial-dev libatlas-base-dev libjasper-dev  libqtgui4  libqt4-test
sudo pip3 install numpy
sudo pip3 install --no-cache-dir opencv-python-headless
```

## Usage

Download/Clone this repository to a directory and run `python3 CardDetector.py` from that directory. 

The program allows you to use either a PiCamera or a USB camera. Make sure to enable the camera access for the pi using `sudo raspi-config` --> Interface Option --> Enable Camera. **If using a USB camera, change line 38 in CardDetector.py to the following :**
```
videostream = VideoStream.VideoStream((IM_WIDTH,IM_HEIGHT),FRAME_RATE,2,0).start()
```
Cards need to be placed on a dark background for the detector to work. Press 'q' to end the program.

## Improve the performance by providing better images

The card detector will work best if you use isolated rank and suit images generated from your own cards. To do this, run Rank_Suit_Isolator.py to take pictures of your cards. It will ask you to take a picture of an Ace, then a Two, and so on. Then, it will ask you to take a picture of one card from each of the suits (Spades, Diamonds, Clubs, Hearts). As you take pictures of the cards, the script will automatically isolate the rank or suit and save them in the Card_Imgs directory (overwriting the existing images).

### Note for Windows Users

The program was originally designed to run on a Raspberry Pi with a Linux OS, but it can also be run on Windows 7/8/10. To run on Windows, download and install Anaconda (https://www.anaconda.com/download/, Python 3.6 version), launch Anaconda Prompt, and execute the program by launching IDLE (type "idle" and press ENTER in the prompt) and opening/running the CardDetector.py file in IDLE. The Anaconda environment comes with the opencv and numpy packages installed, so you don't need to install those yourself. If you are running this on Windows, you will also need to change the program to use a USB camera, as described below.


## Code

- CardDetector.py contains the main script

- Cards.py has classes and functions that are used by CardDetector.py

- PiVideoStream.py creates a video stream from the PiCamera, and is used by CardDetector.py

- Rank_Suit_Isolator.py is a standalone script that can be used to isolate the rank and suit from a set of cards to create train images

- Card_Imgs contains all the train images of the card ranks and suits



