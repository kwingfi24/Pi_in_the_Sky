This is where we will keep tabs on our progress during the duration of this project.


### Feb 15, 2022
Kaitlyn - The Accelerometer and display screen are finished as of today. They will need to be tested and tweaked during the tstin gof different prototypes, but they should work relatively well. I also have started on the camera. I did not get too far with this today. I hope to have it finished by Thursday or mid Tuesday at the latest. There is no school on Monday, but I'm not too worried about losing the day. It was sort of planned for in the schedule.

Christian - 

### Feb 17, 2022
Kaitlyn - I got the camera working half way today. I will have to work over the weekend or push it over to Tuesday next week. I got the camera to take pictures consecutively every 10 seconds. This also doesn't start until a button is pressed and has a 2 second delay. The part I am struggling to do is make the pictures stop when the button is pressed again. I found a helpful website that explains a lot about the button import. (the link is https://gpiozero.readthedocs.io/en/stable/recipes.html#button)


Christian - 

### Feb 22, 2022
Kaitlyn - I tried different methods such as while loops and defining different things. I'm not ablr to figure out how to stop the program after a certain number of pictures or amount of time. There is a way to take a certain amount of photos but there are way too many to keep up with (it takes a certain amount of photos every second rather than minute). I've been stuck with this. I did see that you could take a video for a second then pause for 2 then record again for 1 second and the repeating. I'm thinking I can take this and use it, but instead of a video have it take pictures.


Christian -

### Feb 24, 2022
Kaitlyn - My idea from Tuesday worked. I found this code from https://www.raspberrypi.com/documentation/accessories/camera.html and it has the pi camera take a picture eafter a certain amount of time (I have it set to every 1 second right now) for a certain amount of time (I have it set for 6 seconds for testing at the moment). The time between each photo and how long it runs for will depend on how long the plane is in the air. It still needs to be a bit worked out, but I'm stepping away to work on another part of the project.


Christian -

### Feb 28, 2022 
Kaitlyn - Today I got the LEDs working and blinking in the way I want. To do this in a simplified way rather than trying to code each light individually, I used a LEDBoard to control them all at once. I'm going to start looking at the code as a whole now, and go back to the pi camera that was giving me so much trouble. So far I think I made the schedule a bit wrong. I should have allowed more time for the actual coding and designing part, butwe aren't too far of course from were we were planning to be at this point in time. Our design has also changed. We are getting rid of the door and falling things, so as of right now the only thing that will happen are the lights going off. Something might need to be added, but that hasn't been decided yet.

Christian -


### Mar 1, 2022 
Kaitlyn - The code below is what I have come up with for the camera code. It is not pretty or convenient, so I'm hoping to find a different way by the end of this project. It still does what it's supposed to do though, because of this I'm still going to use it. In the nano file, I still kept older attempts and helpful code at the bottom in case I revisit. for the second half of class today, I was starting to work on putting the code together. After spending a bit of time with this, I stopped in order to take time to reorganize myself and the project. The updated plan will be in the PLANNING.md as well as touched on in the README.md.

```
import time
from picamera import PiCamera
from gpiozero import Button

button = Button(17)
camera = PiCamera()

# program start with a button press
button.wait_for_press

with picamera.PiCamera() as camera: # this will take 13 photos within 6 seconds
  camera.start_preview()
  time.sleep(2) # this will give us 2 seconds to get the plane in the air before it starts taking pictures
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5) # this will give us half a second before the next picture
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5) # half a second before the program stops
  camera.capture('img{counter:02d}.jpg') #last picture
 ```


Christian -

### Mar 3, 2022 
Kaitlyn - Today I mostly worked on Github, doing the documentation stuff. I personally have been a bit stressed about the coding part recently, and wanted to take a days break while still being productive and working on the project. Along with updating the README.md tab, I also worked on drawing up a nice diagram that can hopefully be used later on too. I'm hoping to be completely done with coding and on to testing in two weeks tops (hopefully it won't take that long). If needed I can also work outside of class to finish rather than holding up the teams progression. 


Christian -

### Mar 7, 2022 
Kaitlyn - I didn't get too far today. I was trying to put all the code together in one thing.


Christian -

### Mar 8, 2022 
Kaitlyn - **NOTE: I switch the working shutdown button for the camera button temporarly due to some difficulties and limited space. You will have to switch it back eventually. Remember the pin for the shutdown button is 21!**


Christian -

### Mar 10, 2022 
Kaitlyn - 


Christian -

### Mar 14, 2022 
Kaitlyn - 


Christian -
