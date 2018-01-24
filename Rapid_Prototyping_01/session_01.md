# Sessions 01 and 02

## Designing and Building Lasercut Prototype Enclosures in Rhino

This is a practical guide with limited scope to building enclosures/interface boxes, please also undertake the [Rhino Essential Training](https://www.lynda.com/Rhino-tutorials/Rhino-5-Essential-Training/133324-2.html) Lynda course.

### Task 1 - Research



### Task 2 - Simple 2D Drawing

#### Interface

![Interface Image](images/interface.png)

Make new Large Objects mm template.

Command line

OSnap

Ortho

Grid Snap

View on panes

#### Line

Type the word "Line", you will see that in the command line, it will start to guess what you want.

Hit Enter when the word "Line" is highlighted in the command line.

In the pane labelled "Top" click on coordinate point 0,0,0. This is the first point of our line.

Now click 20mm above the first point.

If you make a mistake when clicking, just hit escape or click cancel and start again. 

You've drawn your first line!

![Line Image](images/line.png)

OK, now experiment with the "move" command to try moving the line around. What happens if you turn on Ortho (you also have to find it on the interface again!).

##### Options

When you select a particular drawing method, you will be given a set of options. If you're working on a PC these options are selectable using letter keys on the keyboard, these keys are highlighted in the words of the options beneath the command line:

![Line Options PC](images/line_options.png)

On a mac, there are also buttons to select the options:

![Line Options Mac](images/line_options_mac.png)

You can see that we can draw from the centre, and the PC loads of other options are available.

#### Polyline

Now type the word "Polyline". 

Try experimenting with it, what does Polyline mean, based on what happens when you click around in the top pane?

![Line Image](images/polyline.png)

#### Curves

OK, that's all good for straight lines, but what happens if we want a curved line. Try clicking on the curve menu at the top. There are lots of options here, all quite useful but perhaps a bit daunting. Click off the menu and try typing "_curve" into the command line. This will allow us to create a bezier curve through the points we click on the plane. Ensure you are focused in the top view pane again...


Just click around and experiment, can you undo if you made a mistake?

![Curve Image](images/curve.png)

### Task 3 - Extrusion

Extrusion is a process used a lot in CAD and general manufacturing, and it's something we're going to be using a lot whilst we lasercut stuff. It involves creating an object that has a cross-sectional profile that is fixed.

![Extrusion Basic Image](images/uXIEe.png)

#### Rectangle

With the top pane focused, type "rect" and the command line will auto-fill to "Rectangle". Hit enter. In the options, you will be able to select "center", go ahead. 

Click on point 0,0,0 and draw a rectangle that is 30mm wide and 80mm high. HINT: you can type those figures in if you want...

![Rectangle Basic Image](images/rectangle.png)

Now type "extrude" into the command line. 

You can see that you are presented with some options here. We want to make a solid object, so type the letter that makes it *S*olid...

![Rectangle Basic Image](images/extruderect.png)

Great, we created a box! Handily, there is also a "Box" command. But the principle of extrusion is really important to understand...  

#### Circle

Let's do the same with a circle:

Create a circle with a diameter of 100mm.

Then extrude it as a solid cylinder that is 500mm long.

#### Polyline

OK now draw polyline in a shape of your choosing. Make sure that the start and end points are the same so you create what is called a closed curve. Use OSnap End to your advantage.

Now extrude and make your custome shape.

### Task 4 - Split/Boolean Split

The "Split" function is another incredibly useful tool in our inventory. It uses one object to cut another. Let's try it with two lines:

#### Lines

Draw one line 10mm long. Then, use OSnap to snap to the midpoint of this line and draw another line which intersects it halfway along at a right angle.

Click on the first line and type "Split". Now click on the second line and hit enter.

![Rectangle Basic Image](images/split_line.png)

Now you have three lines!


#### Cylinder

Create a cylinder by typing the word "Cylinder" into the command line. Make a cylinder that is 80mm diameter and 200mm long.

#### Box

Now make a box that starts on the midpoint of one side of the cylinder. Use Osnap to your advantage here. 

OK, type the command "Boolean Split" into the command line and hit enter. When prompted for the object to split, select the cylinder and hit enter. When prompted for cutting object, select the box and hit enter.

Now delete the box and you should see that you have split the cylinder into a custom shape.

![Boolean Split](images/boolean_split_01.png)

#### Sphere

Now try the same thing but using the sphere command. Make sure it intersects with the end of the custom cylinder. Using "OSnap center" to your advantage so that it snaps to the right point.

Now do boolean split in an order of your choosing - will you split the cylinder or the sphere?

I split the sphere and deleted the cylinder:

![Boolean Split](images/boolean_split_02.png)

### INTERLUDE 1 - MATERIAL THICKNESS

When creating designs for lasercutting, it is critical that we know the thickness of the sheet material we are cutting. 

For this project, we will cut a 5mm plywood. That is pretty thick, but at least we will know it is strong. 

### INTERLUDE 2 - ARDUINO MODEL

So, we now know how thick the walls of our box will be, but how do we know how big to make the box?

This is where the power of the interplex comes into play for us: someone somewhere will have thought of this already, and will have made a 3D model of an Arduino board.

Some cursory research resulted in me finding this: [Arduino 3D model](https://grabcad.com/library/arduino-uno-r3-1). You'll need to register an account to download it. Make sure you put it in the same directory where your Rhino project is located. Because you've definitely saved already, right? That would be crazy to start working on a new project and save your work...

OK, now go to file->import and import the file called "arduino uno.STEP". Select the default import settings et voila, we have our very own Arduino Uno sitting in space. 

You have to figure this one out: you need to *rotate* the Arduino by 90 degrees so it lies flat on the Y Plane. HINT: Use Ortho to your advantage. Take Osnap off and rotate around point 0,0,0.

![Arduino Rotate](images/arduino_rotate.png)

![Arduino in Position](images/arduino.png)

Now put Osnap on End, and type the command "move". Hover your cursor over the very bottom of the pins on the underside of the board in the Front view pane. Let the cursor snap to the bottom of the pin. Now move the board up so it sits about 5mm above the X axis.


### Task 5 - Using Layers

As with Adobe products, Rhino (as other CAD programmes) implements a system of layers. Layers are incredibly useful when working with more complex designs, as it means you can logically group objects and turn visibility on and off to aid understanding.

The layers pane is located to the right hand side. The lightbulb symbol is for visibility. You can also lock the layer to prevent changes.

As you can see when we made our new project from the template, we automatically had 6 layers created for us. By double clicking on the name, you can edit it. Let's change the first three layers to have the names "Sides_X", "Sides_Y" and "Top_Bottom".

Let's also put the Arduino on it's own layer. Rename one of the other layers. Then click on the Arduino so it is selected, then right click on your Arduino layer in the Layers pane and select "Move Objects to Layer"

#### First side of box

Maximise the top view by double clicking in the top left hand corner, where it says "Top".

Now draw a rectangle (120mm x 160mm) whose bottom side is level with the USB port of the Arduino, this will help us to see the total area of our box:

![Boolean Split](images/arduino_rectangle.png)



##### Using the mirror function

#### Second side of box



#### Third side of box

### Task 6 - Construction lines

### Task 7 - Cutting objects

### Task 8 - Adding screw and USB port holes

### Task 9 - Adding text to be engraved

### Task 10 - Adding ventilation holes

### Task 11 - Using Make2D to get surface outlines

### Task 12 - Arranging your 2D shapes for cutting

### Task 13 - Open Challenge: Add Handles

### Task 14 - Open Challenge: Add a lid

### Task 15 - Open Challenge: Add a pattern to be cut on one side

### Task 16 - Open Challenge: Add holes/mountings for buttons

http://www.instructables.com/id/Laser-Cut-Boxes/

https://grabcad.com/library/arduino-uno-r3-1


