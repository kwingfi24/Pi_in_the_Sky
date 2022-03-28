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
Kaitlyn - **NOTE: I switch the working shutdown button for the camera button temporarly due to some difficulties and limited space. You will have to switch it back eventually. Remember the pin for the shutdown button is 21!** After changing the buttons, I got everything to work. Everything, excluding the lights and button for now, are working together. I'm hoping by the end of next class, I will have the button figured out(starting and stopping the things from running), so I can then also move onto soldering a custom circuitboard. We are hoping to have everything soldered and on the plane for testing by next Tuesday or Thursday. We will then move n to the test and refining process. 

Christian -

### Mar 10, 2022 
Kaitlyn - I have recorded the pins for everything to be used at a lter time while soldering. I tried a way to get the things starting and stopping on the same button, but I have not yet succeded. I'm taking the pi home to work on over the weekend to get this button figured out. On Monday, I hope to be soldering. this will allow us to test all of Tuesday, and know what is working and what isn't.

Christian -

### Mar 14, 2022 
Kaitlyn - We have no singleton this week and Friday off. After a busy weekend, I was unabe to finish the button. I'm going to work on this all class, hopefully completing it. If not, I will take it home and finish it by Thursday. This will allow us Wednesday and Monday to solder. Leaving the rest of the time before spring break to testing.

Christian -

### Mar 16, 2022
Kaitlyn - I have gotten everything ready for soldering. The button code that I was working on had one single coding error that was fixed pretty easily. I'm now working on the wiring diagram, then moving on to soldering it all together. This will probably take the singleton and block day next week. This would mean that we would be testing next Thursday. By the start of spring break, we will have tested the plane and know what works and what didn't.

Christian - 

### Mar 21, 2022
Kaitlyn - Being a short day and being unable to have a quick recap on soldering, I made a diagram and updated Github on the documantation end. I also realized that during this first test, I forgot that I have not yet programmed the lights to go off at the appex, which is a big part of the project. For now we are going to test without them, seeing how things work. This will  give me time to do the coding while the design of the plane is being modified to fly better. 

Christian - 

### Mar 22, 2022
Kaitlyn - Due to again being unable to solder today, I got started on the lights going off at the apex. I'm struggling a bit, but I hope to possibly get this done before we test the first time.

Christian - 

### Mar 28, 2022
Kaitlyn - There was more delay today. My pi is not responding with my computer, therefore enabling me from doing work. I'm getting codes sying that the device was not found or if there is one found, it is not loading or allowing me any further (not even to the login part). Instead today I will e researching and updating Github. I also will be working on code still, but wothout a way to test I don't think I'll get very far. I will check again periodically through out class today to see if I am able to get on.

(After waiting 5 minutes and pressing enter every so often)
![Screenshot 2022-03-28 9 15 57 AM](https://user-images.githubusercontent.com/60272021/160406151-7566cee2-0ba1-4674-9e5a-26d3312d40f6.png)

(Another attempt where the pi isn't even recognized)
![Screenshot 2022-03-28 9 16 35 AM](https://user-images.githubusercontent.com/60272021/160406319-08b5e3eb-57d3-4544-9cc1-b9a77ec8577e.png)

Christian - 

### Mar 30, 2022
Kaitlyn - 

Christian - 
