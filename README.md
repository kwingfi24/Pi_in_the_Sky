# Pi_in_the_Sky
Engineering 4 - Project

## Table of Contents
* [Planning](#Planning)
* [One_Month_Check_In](#One_Month_Check_In)
* [Test_1](#Test_1)
---

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

### Bill of Materials
- LSM303
- OLED Display
- Pi Camera
- 2 Buttons
- 2 LEDS
- 2 Servos
- Switch
- Rubberband

Materials
- Cardboard for wings
- Wood for plane body
- 3D printed nose

### Milestones
- [x] Brainstorm ideas
- [X] Develop an initial design (pencil and paper, CAD, etc.)
- [ ] Construct a prototype
- [ ] Test your design
- [ ] Refine/optimize your design
- [ ] Present finished product

## One_Month_Check_In
#### This update is from March 1 (a month after the project has started)
### What have we done?
In this month we have made a design for the plane and have printed mutiple to test the flight capability of it. There has been a total of 3 versions of the plane that change size, center of gravity points, and angles of wings. We have also finished most of the code other than a few things. The lights have been figured out, the accelerometer/OLED screen is done, and most of the iring is pretty final. So far we have been able to stay mostly on schedule, but we have run into a few bumps where we had to spend an extra bit of time on some things. We have found multiple helpful websites that have helped along the way.

### What still need to be done?

A few tasks still need to be done befre we can move onto the testing and refining stages of the project. On the coding/wiring side of things, the code working together and without being attached to a computer still needs to be figured out. Making it battery operated and soldering pieces together also needs to be completed within the next few weeks.

### Where are we struggling?

The planes keep flipping going front first. There was too much weight in the front, so we changed the design. We are trying to distribute the weight evenly, but without the pi and everything inside, it is a bit difficult to gage. We are waiting to change it anymore until we are able to test everything together for the first time. The pi camera gave us a lot of trouble. I tried many different ways and still have not settled on a particular one. 

### What has been changed?
The plane is no longer closed, rather it is two sides with an open middle. It is also going to be made only out of cardboard to improve durability and weight. The wings have also changed a lot. There are now two sets of wings. In the final design (for now) both set of wings are curved and angled. We are no longer going to be dropping things from the plane. There will only be lights as of right now. We got rid of the things falling to get rid of some of the weight and in the interest of time. We could possibly add this or another thing back to the project if time allows. 

### Bill of Materials
- LSM303
- OLED Display
- Pi Camera
- 2 Buttons
- 6 LEDS
- Switch
- Rubberband

Materials
- Cardboard

### Pictures/Diagrams
##### Design
Link to Onshape Document: https://cvilleschools.onshape.com/documents/492561168bf6b91a97d77a47/w/45d7efb3da141b22b711ac96/e/4b3a4ccdc809ca3a080ae7f4

Final Printed - Angled and curved wings

![Screenshot 2022-03-03 10 24 57 AM](https://user-images.githubusercontent.com/60272021/156595463-9ebacbb5-0c09-4814-a178-cf23a2143108.png)

##### Wiring
Wiring - Better pictures/diagrams will come

![Screenshot 2022-03-03 9 36 39 AM](https://user-images.githubusercontent.com/60272021/156586159-3fd2d8d5-d540-4465-90f7-1111caf976b9.png)

##### Code snipets

Accelerometer/OLED Screen
```
while True:    
    accel, mag = lsm303.read()
    # Grab the X, Y, Z components from the reading and print them out.
    accel_x, accel_y, accel_z = accel
    mag_x, mag_y, mag_z = mag

    # change in x and z values
    a = direction(x)
    b = direction(height)
    
    # "Graphing" the x values by drawing circles/plotting point every second
#    draw.ellipse((x+50+a, top+25, x+shape_width+50+a, bottom-25), outline=225, fill=225) # x values
#    draw.ellipse((x+50, top+b, x+shape_width+50, top+shape_height+b), outline=225, fill=225) # z values
    draw.ellipse((x+a, top+b, x+shape_width+a, top+shape_height+b), outline=225, fill=225) # both values
    
    
    # Write readings for x and y
    draw.text((x, bottom-10), f'X: {(round (quotient(accel_x, scale), 2))}',  font=font, fill=255)
    draw.text((x+60, bottom-10), f'Z: {(round (quotient(accel_z, scale1), 2))}', font=font, fill=255)
    # Wait half a second and repeat.
    time.sleep(.5)
    # Display image.
    disp.image(image)
    disp.display()
    # clear just the bottom leaving the points there to look at
    draw.rectangle((0,bottom-20,width,bottom), outline=0, fill=0)
```
Pi Camera
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
LEDS
```
leds.on()
sleep(1)
leds.off()
sleep(1)
leds.value = (1, 0, 0, 0, 0, 1)
sleep(1)
leds.value = (0, 0, 1, 1, 0, 0)
sleep(1)
leds.value = (0, 1, 0, 0, 1, 0)
sleep(1)
leds.blink()
```

## Test_1
### How did it go?
### What worked and what didn't?
##### Code: 
Comments are in the code
```
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
# Create a LSM303 instance.
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
    print('Press the left (yellow) button to start. Press the right (grey) button to stop.')
    while True:
        input_state = GPIO.input(leftbutton) # reading the button state until pressed
        if input_state == False:
            print('left button was pressed!')
            sleep(2)  
            while True: 
               input_state1 = GPIO.input(rightbutton)
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
               # Display image.
               disp.image(image)
               disp.display()
               # clear just the bottom leaving the points there to look at
               draw.rectangle((0,bottom-20,width,bottom), outline=0, fill=0)
        
               with PiCamera() as camera: 
                   camera.start_preview()
                   camera.capture('/home/pi/Documents/Pi_in_the_Sky/pics/Mar22-%s.jpg' % frame) # adding numbers to pictures
                   frame += 1
                   sleep(.5)
               if input_state1 == False: 
                     print('right button was pressed!')
                     break

finally:
    GPIO.cleanup()  
```
### What needs to be changed/improved? 
### Pictures 
##### Of plane 
##### From flight
