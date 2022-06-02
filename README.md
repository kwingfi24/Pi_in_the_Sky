# Pi_in_the_Sky
Engineering 4 - Project Documentation

## Table of Contents
* [Bill_of_Materials](#Bill_of_Materials)
* [CAD_Renderings](#CAD_Renderings)
* [Actual_Photos](#Actual_Photos)
* [Diagram_of_Circuit](#Diagram_of_Circuit)
* [Commented_Code](#Commented_Code)
* [Planning](#Planning)
* [Design_Decisions](#Design_Decisions)
* [Process_and_Schedule](#Process_and_Schedule)
* [Problems_and_Errors](#Problems_and_Errors)
---

## Bill_of_Materials
- LSM303
- OLED Display
- Pi Camera
- 3 Buttons
- 6 LEDS
- Switch
- Rubberband

Plane
- Cardboard

## CAD_Renderings
Link to Onshape Document: https://cvilleschools.onshape.com/documents/492561168bf6b91a97d77a47/w/45d7efb3da141b22b711ac96/e/4b3a4ccdc809ca3a080ae7f4
### Version 3 (Final as of right now)
![Screenshot 2022-03-03 9 52 52 AM](https://user-images.githubusercontent.com/60272021/156589460-5ff91dea-edbb-4563-aca9-adfe65bd77a1.png)

## Actual_Photos
### Version 1
![Screenshot 2022-03-03 9 59 49 AM](https://user-images.githubusercontent.com/60272021/156590828-7085db7d-46a6-4710-9ebc-519f81f610b8.png)
### Version 2 - Added a second set of wings
![Screenshot 2022-03-03 10 00 05 AM](https://user-images.githubusercontent.com/60272021/156590900-1bf0d4be-968a-4302-82c7-9ed34e270bba.png)
### Final Printed - Angled and curved wings
![Screenshot 2022-03-03 10 24 57 AM](https://user-images.githubusercontent.com/60272021/156595463-9ebacbb5-0c09-4814-a178-cf23a2143108.png)

## Diagram_of_Circuit
![Screenshot 2022-06-02 10 28 17 AM](https://user-images.githubusercontent.com/60272021/171652804-9e8845a0-1033-4325-bc07-c98eba40f952.png)


## Commented_Code
```
# Started Mar 1
# Finished on Mar 16 (first test)
# This will be the code that will be running.
# It combines the parts together, including 
# the accelerometer, OLED screen, and the camera. 
# It doesn't include the lights yet.

# All the imports

from time import sleep
import RPi.GPIO as GPIO

GPIO.setmode(GPIO.BCM)
GPIO.setwarnings(False)

# for acceerometer and OLED screen
import Adafruit_GPIO.SPI as SPI
import Adafruit_SSD1306
import Adafruit_LSM303
from PIL import Image
from PIL import ImageDraw
from PIL import ImageFont

# for LEDS
from gpiozero import LEDBoard
from signal import pause

# for camera
from picamera import PiCamera
from gpiozero import Button


# Defining things (accelerometer and OLED + one for the camera)
# Create a LSM303 instance
lsm303 = Adafruit_LSM303.LSM303()

scale = int (9.81)
scale1 = int (100)

def quotient(accel_x, scale): 
    return (accel_x / scale)
def quotient(accel_y, scale): 
    return (accel_y / scale)
def quotient(accel_z, scale1): 
    return (accel_z / scale1)
    
def direction(x):
    return (quotient(accel_x, scale) * 4)
def direction(height):
    return (quotient(accel_z, scale1) * 1.5)

# Camera
frame = 1

prev = 0

# Pins for each thing

leftbutton = 20
rightbutton = 18

GPIO.setup(leftbutton, GPIO.IN, pull_up_down=GPIO.PUD_UP)
GPIO.setup(rightbutton, GPIO.IN, pull_up_down=GPIO.PUD_UP)

# Accelerometer and OLED screen
RST = 24
# Note the following are only used with SPI:
DC = 23
SPI_PORT = 0
SPI_DEVICE = 0

# LEDs
leds = LEDBoard(26, 19, 13, 6, 5, 22)

# accelerometer setup
disp = Adafruit_SSD1306.SSD1306_128_64(rst=RST, i2c_address=0x3d)
# Initialize library.
disp.begin()

# Clear display.
disp.clear()
disp.display()

# Create blank image for drawing.
# Make sure to create image with mode '1' for 1-bit color.
width = disp.width
height = disp.height
image = Image.new('1', (width, height))

# Get drawing object to draw on image.
draw = ImageDraw.Draw(image)

# Draw a black filled box to clear the image.
draw.rectangle((0,0,width,height), outline=0, fill=0)

# First define some constants to allow easy resizing of shapes.
padding = 5
shape_width = 2
shape_height = 2
top = padding
bottom = height-padding
# Move left to right keeping track of the current x position for drawing shapes.
x = padding

# Load default font.
font = ImageFont.load_default()

    

try:
    print('Press the green button to start. Press the red button to stop.')
    while True:
        input_state = GPIO.input(leftbutton) # reading the button state until pressed
        if input_state == False:
            print('start button was pressed!')
            sleep(2) # this will give us 2 seconds to get the plane in the air before the accessories start 
            while True: # This while loop will keep running until the right button is held down for .5 seconds
               input_state1 = GPIO.input(rightbutton) # this will read the right button state, taking it to the if statement
               accel, mag = lsm303.read()
               # Grab the X, Y, Z components from the reading and print them out.
               accel_x, accel_y, accel_z = accel
               mag_x, mag_y, mag_z = mag

               # change in x and z values
               a = direction(x)
               b = direction(height)
    
               # "Graphing" the x values by drawing circles/plotting point every second
               draw.ellipse((x+a, top+b, x+shape_width+a, top+shape_height+b), outline=225, fill=225) # both values
    
    
               # Write readings for x and y
               draw.text((x, bottom-10), f'X: {(round (quotient(accel_x, scale), 2))}',  font=font, fill=255)
               draw.text((x+60, bottom-10), f'Z: {(round (quotient(accel_z, scale1), 2))}', font=font, fill=255)
               # Wait half a second and repeat.
               # Display image.
               disp.image(image)
               disp.display()
               # clear just the bottom leaving the points there to look at
               draw.rectangle((0,bottom-20,width,bottom), outline=0, fill=0)
               #with PiCamera() as camera: # 
                   #camera.start_preview()
                   #camera.capture('/home/pi/Documents/Pi_in_the_Sky/pics/test-%s.jpg' % frame) # adding numbers to pictures
                   #frame += 1
               print('pic')
               print(b)
               sleep(.5)
               if (b < prev): # when it hits the apex, lights will start blinking
                   leds.value = (1, 1, 1, 1, 1, 1)
                   #sleep(1)
                   leds.value = (0, 0, 0, 0, 0, 0)
                   #sleep(1)
                   leds.value = (1, 0, 0, 0, 0, 1)
                   #sleep(1)
                   leds.value = (0, 0, 1, 1, 0, 0)
                   #sleep(1)
                   leds.value = (0, 1, 0, 0, 1, 0)
                   #sleep(1)
                   leds.blink()
                   if input_state1 == False: # when the right button is pressed and held, it will come here and stop the code
                        print('stop button was pressed!')
                        break
                        # Display image.
                        disp.image(image)
                        disp.display()
                        # clear just the bottom leaving the points there to look at
                        draw.rectangle((0,bottom-20,width,bottom), outline=0, fill=0)
                        draw.text((x, bottom-10), f'The apex of this flight was ___',  font=font, fill=255)
               b = prev
               if input_state1 == False: # when the right button is pressed and held, it will come here and stop the code
                        print('stop button was pressed!')
                        break
                        # Display image.
                        disp.image(image)
                        disp.display()
                        # clear just the bottom leaving the points there to look at
                        draw.rectangle((0,bottom-20,width,bottom), outline=0, fill=0)
                        draw.text((x, bottom-10), f'The apex of this flight was ___',  font=font, fill=255)

finally:
    GPIO.cleanup()          
```
## Planning
### Scope and Function
#### How will the final product function?
In this project we will be making a plane with hang glider like wings. Within the plane glider, there will be a pi along with some other things to take some data of the flight as well as pictures. The OLED Display and accelerometer will be used to graph the movement of the plane glider while a pi camera will be taking pictures of the ground from the bottom of the glider. 

#### What materials will be needed and how much?
For the wings, we will be using cardboard. Most of the body of the plane will be in wood, but with a 3D printed nose in order for it to be in a more rounded shape. We are making the plane glider as small as possible to keep it light and easy to launch, so we will not be using a lot of materials. The most material will be the wood due to the octogonish shape of the plane glider. However, due to the size, we should be able to get by with only a sheet or two of wood with the same thickness as the acrylic. Wood is being used rather than acrylic so that it can withstand a bit more of an impact. 

#### What do you still need to learn for the project?
We need to learn a bit more about how the accelerometer and OLED display work. Graphing the flight without filling the screen could be a problem. To accommodate for this, we might need a bigger OLED screen, but I’m not seeing any in the lab. Instead we might need to graph fewer points rather than all of them to not fill the screen. We also will need to learn how to have things falling from the plane glider without interfering with the flight. This should be combated with them being released facing the opposite direction of the plane glider’s flight. If this does not work, changes will need to be made with either a change of what is dropping, how much is dropping, and the falling speed/time of the objects falling. 

#### What is the definition for "success" in the project?
The definition of success for this project will be growing and learning about things we didn’t previously know, having a working project by the middle of May, and getting some awesome pictures from the flight.

### Diagram
Paper:
![image](https://user-images.githubusercontent.com/60272021/153009169-bfc58da1-c097-4e1e-9e28-fedd38d4bfe2.png)

Onshape:
![pic of plane feb 10](https://user-images.githubusercontent.com/60272021/160408978-b35b7c67-3a37-4182-a20d-794159987845.png)

## Design_Decisions

The plane is no longer closed, rather it is two sides with an open middle. It is also going to be made only out of cardboard to improve durability and weight. The wings have also changed a lot. There are now two sets of wings. In the final design (for now) both sets of wings are curved and angled. We are no longer going to be dropping things from the plane. There will only be lights as of right now. We got rid of the things falling to get rid of some of the weight and in the interest of time. We could possibly add this or another thing back to the project if time allows.

## Process_and_Schedule
### Milestones
- [x] Brainstorm ideas
- [X] Develop an initial design (pencil and paper, CAD, etc.)
- [X] Construct a prototype
- [X] Test your design
- [ ] Refine/optimize your design
- [ ] Present finished product
### Schedule
We had planned for this project to last for 15 and a half weeks. Starting on Feb 1 (Including planning time) and ending on May 19. Presentation day is May 26.
We did not meet this goal...
- [x] Initial Design (paper) including rough measurements - Tues, Feb 8
- [x] Accelerometer and OLED Display - Tues, Feb 15
- [x] Initial Design (CAD) including any measurements - Thurs, Feb 17
- [x] Pi Camera with button - Mon, Feb 28
- [x] Lights for apex - Mon, Feb 28
- [X] Testing flying capability of original design - Mon, Feb 28
- [X] Putting pieces of the code together - Tues, Mar 1  
- [X] Working with no screen - Thurs, Mar 10
- [ ] Battery powered - Thurs, Mar 10
- [x] Build prototype #1 (possibly testing without all pieces)- Thurs, Mar 13
- [x] Testing that prototype - Tues, Mar 14
- [x] Tweaking design and/or code - Mon, Mar 15
- [X] Build prototype #2 / Update prototype #1 - Tues, Mar 16
- [X] Testing that prototype - Thurs, Mar 17
- [X] Tweaking design and/or code - Mon, Mar 21
- [ ] Finalize CAD Design - Mon, Mar 28
- [x] Wiring condensed - Tues, Mar 22
- [x] Diagram and commented code - Tues, Mar 22
- [ ] Soldering - Mon, Mar 28
- [x] Build launcher prototype - Thurs, Mar 31
- [x] Testing launcher - Mon, Apr 4
- [X] Tweaking and retesting - Thurs, Apr 7 (Work on this until stuff is done printing/cutting)
- [x] Printing/Cutting - Thurs, Apr 7 (May change do to fast or slow printing/cutting)
- [x] Assembly - Tues, Apr 12
- [ ] Testing and small tweaks - Thurs, May 19
- [X] Documantation and Github organizing/update or any final presentation parts - Tues, May 24
- [ ] Presenting finished product - Thurs, May 26
### Monthly Check-in
#### March - 1 Month
What have we done?

In this month we have made a design for the plane and have printed multiple to test the flight capability of it. There have been a total of 3 versions of the plane that change size, center of gravity points, and angles of wings. We have also finished most of the code other than a few things. The lights have been figured out, the accelerometer/OLED screen is done, and most of the wiring is pretty final. So far we have been able to stay mostly on schedule, but we have run into a few bumps where we had to spend an extra bit of time on some things. We have found multiple helpful websites that have helped along the way.

What still needs to be done?

A few tasks still need to be done before we can move onto the testing and refining stages of the project. On the coding/wiring side of things, the code working together and without being attached to a computer still needs to be figured out. Making it battery operated and soldering pieces together also needs to be completed within the next few weeks.

#### May - 2 Months (This is after the one month break for Onshape)
What still need to be done?

Design/Cut

Until testing, there isn't a ton we can do here, but we possibly will need to change things depending on how it works while testing. It is very possible that a design change will be necessary. We also need to figure out placement and attachment of the pieces. 

Coding/Wiring

Sadly, the few tasks from the one month still need to be done before we can move onto the testing and refining stages of the project. We had trouble with the pi and it hung us up, but the code is complete. On the coding/wiring side of things, the code working together and without being attached to a computer still needs to be figured out. Making it battery operated and soldering pieces together also needs to be completed within the next few weeks.

Overall

Overall we still need to test with the weight on the plane and tweak from there. After all of the tweaking, we will need to finalize the design as well as the code, eventually ending with the presentation of the final. There is also a week where we are going to lose time due to 2 hour delays, and another week where one teammate will not be here. To get around this, we will have to work fast, but careful to not make too many mistakes as well as possibly spending extra time in the lab before, after, and during the school day.
### Day to Day Progress
We kept track of what we were doing. For a closer look at that you can go here: https://github.com/kwingfi24/Pi_in_the_Sky/blob/main/DAILY_DOCUMENTATION.md

## Problems_and_Errors

1 - The planes keep flipping going front first. There was too much weight in the front, so we changed the design. We are trying to distribute the weight evenly, but without the pi and everything inside, it is a bit difficult to gauge. We are waiting to change it anymore until we are able to test everything together for the first time. 

2 - The pi camera gave us a lot of trouble. I tried many different ways and settled on taken one picture at a time while having it in a loop. 


Previous:
```
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
  time.sleep(.5) # half a second before the program stops
  camera.capture('img{counter:02d}.jpg') #last picture
```



Now: (other stuff has been cut out of the while loop to just show the camera)
```
       while True: 
            with PiCamera() as camera: 
                   camera.start_preview()
                   camera.capture('/home/pi/Documents/Pi_in_the_Sky/pics/____-%s.jpg' % frame) # adding numbers to pictures *put date where ____ is
                   frame += 1
                   sleep(.5)
```

3 - There ws a struggle with the buttons, but they were simple fixes such as the wiring or button not being in all the way.

4 - My pi wasn't responding with my computer, therefore enabling me from doing work. I was codes sying that the device was not found or if there is one found, it was not loading or allowing me any further (not even to the login part). I eventually had to use SSH.

(After waiting 5 minutes and pressing enter every so often)
![Screenshot 2022-03-28 9 15 57 AM](https://user-images.githubusercontent.com/60272021/160406151-7566cee2-0ba1-4674-9e5a-26d3312d40f6.png)

(Another attempt where the pi isn't even recognized)
![Screenshot 2022-03-28 9 16 35 AM](https://user-images.githubusercontent.com/60272021/160406319-08b5e3eb-57d3-4544-9cc1-b9a77ec8577e.png)
