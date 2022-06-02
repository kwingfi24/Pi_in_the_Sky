# Pi_in_the_Sky
Engineering 4 - Project Documentation

## Table of Contents
* [Bill_of_Materials](#Bill_of_Materials)
* [CAD_Renderings](#CAD_Renderings)
* [Actual_Photos](#Actual_Photos)
* [Diagram_of_Circuit](#Diagram_of_Circuit)
* [Commented_Code](#Commented_Code)
* [Planning](#Planning)
* [Design_Decisions](#)
* [Process_and_Schedule](#)
* [Problems_and_Errors](#)
---

### Bill_of_Materials
- LSM303
- OLED Display
- Pi Camera
- 3 Buttons
- 6 LEDS
- Switch
- Rubberband

Plane
- Cardboard

### CAD_Renderings
Link to Onshape Document: https://cvilleschools.onshape.com/documents/492561168bf6b91a97d77a47/w/45d7efb3da141b22b711ac96/e/4b3a4ccdc809ca3a080ae7f4


### Actual_Photos
Final Printed - Angled and curved wings

![Screenshot 2022-03-03 10 24 57 AM](https://user-images.githubusercontent.com/60272021/156595463-9ebacbb5-0c09-4814-a178-cf23a2143108.png)

### Commented_Code

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
