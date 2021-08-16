# Swing-Helper
This tool has been designed for use in introductory level computer science courses that use java.  The general idea is that it can be built into a jar file and then imported, and used in a project.  Generally, a large problem in introductory courses is that students need to have a pretty firm understanding of objects to create games and animations.  This means that first year students will have a hard time creating anything really cool.  This tool is designed to take away the complexity of making a game for introductory level students.

## **How to setup**
You can download the entire project and build it into a jar file, and then import the jar file into your project.

OR

You can just download the included jar file.
Jar location is : Swing-Helper/Swing-Helper/out/artifacts/SwingHelper_jar/

You should use the following import statement in your project: import clara.Canvas;

## **How to use**
To use this library to all you need to do is create a Canvas object and specify the size the Canvas.  You will likely call methods from this instance of the Canvas class from a game loop.  See the demo below.
```
Canvas canvas = new Canvas(500,500); //create a canvas to draw on
int x = 50;
while(true){ 
//game loop
    canvas.drawColor(Color.BLUE); 
    //change draw color to blue
    canvas.drawOval(x,50,20,20,true); 
    //draw an oval at (x,50) with height and width of 20 and fill it in with a solid color
    x++;
    canvas.repaint(); 
    //draw everything on the canvas that you specified in your code
    canvas.addDelay(5);
    //add a short 5 ms delay
}
```
## **How does this Canvas file work?**

The Canvas file is used to create DrawObjects which can contain information about ovals, rectangles, images, or other items you may want to draw on the canvas.  You can also change the color or rotation when you draw and item to the canvas via a DrawObject as well.  
The main idea is that when you create a Canvas in the runner class you can call methods that appear to draw ovals or rectangles on the screen.  What actually happens is the DrawObject is created and it is added to a queue.  When you call the repaint method all of the DrawObjects are visited in the same sequence that you added them, and they are drawn on the screen. Rotation objects are dealt with the same way.  They are added to the queue and the commands are executed in sequence when the screen is repainted.  There is one small exception here.  When each of the rotation commands is executed they rotate the canvas, and the command is also added to a stack.

The reset method can be used to take all of the rotation commands that have been run and reverse them via the stack.  This only needs to be done if you want to reset the rotation before you repaint the screen.  After you repaint the screen the rotations will all be lost and everything will revert to the original rotation.  The natural functionality of the stack will allow these commands to be run in the reverse order that they were entered which is needed since the rotations will all compound on top of each other. 

## **Method Descriptions**


### **public void drawOval(int x,int y,int width,int height, boolean fill)**

Adds an oval to the drawing queue that will be drawn to the screen at coordinates x,y when repaint is called.  Coordinates provided will specify the top left corner of the drawn object.

Parameters:<br />
x – x position of the oval<br />
y – y position of the oval<br />
width – width of the oval<br />
height – height of the oval<br />
fill – determines if the oval will be filled with the current specified color<br />


### **public void drawRect(int x,int y,int width,int height, boolean fill)**

Adds a rectangle to the drawing queue that will be drawn to the screen at coordinates x,y when repaint is called.  Coordinates provided will specify the top left corner of the drawn object.

Parameters:<br />
x – x position of the rectangle<br />
y – y position of the rectangle<br />
width – width of the rectangle<br />
height – height of the rectangle<br />
fill – determines if the rectangle will be filled with the current specified color<br />


### **public void drawText(String text, int x, int y)**

Adds a text object to the drawing queue that will be drawn to the screen at coordinates x,y when repaint is called.  Coordinates provided will specify the top left corner of the drawn object.

Parameters:<br />
text - the text to display on the screen<br />
x – x position of the rectangle<br />
y – y position of the rectangle<br />



### **public void drawColor(Color color)**

Adds an object to the queue that will change the color of all graphics  ahics drawn to the screen.

Parameters:<br />
color - the new color to be used for all objects to be drawn<br />



### **public void rotate(double rotation, int x, int y)**

Adds a rotation object to the queue. Rotates the entire screen by the specified amount around the given pivot point.  This rotation will hold until repaint is called or the user rotates it back to the original orientation.  

Parameters:<br />
rotation - the amount to rotate the screen in degrees<br />
x - x pivot location<br />
y - y pivot location<br />



### **public String returnKey()**

Returns the key pressed for the current frame being drawn on the screen.

Parameters:<br />
none

Returns:<br />
A string that represents the key pressed



### **public void reset()**

Clears out all drawing and rotational information.  This will not need to be called after repaint.

Parameters:<br />
none



## **How to contribute**
This code base can certainly be optimized, and more features can be added.  Feel free to make changes or improvements.  Please rebuild the jar file when you make changes, so any teachers or students that download the project have access to it.  Keep in mind that this project is intended for use by students, so please make sure it is easy and straight forward to use.  Please do not change the package structure or dedication :)

