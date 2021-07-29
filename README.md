# Swing-Helper
This tool has been designed for use in introductory level computer science courses that use java.  The general idea is that it can be built into a jar file and then imported, and used in a project.  Generally, a large problem in introductory courses is that students need to have a pretty firm understanding of objects to create games and animations.  This means that first year students will have a hard time creating anything really cool.  This tool is designed to take away the complexity of making a game for introductory level students.

## **How to setup**
You can download the entire project and build it into a jar file, and then import the jar file into your project.

OR

You can just download the included jar file.

You should use the following import statement in your project: import clara.Canvas;

## **How to use**
To use this library to all you need to do is create a Canvas object and specify the size the Canvas.  You will likely call methods from this instance of the Canvas class from a game loop.  See the demo below.
```
Canvas canvas = new Canvas(500,500); //create a canvas to draw on
int x = 50;
while(true){ //game loop
    canvas.drawColor(Color.BLUE); //change draw color to blue
    canvas.drawOval(x,50,20,20,true); drawn an oval on the screen at location (x,50) with height and width of 20 and fill it in with a solid color
    x++;
    canvas.repaint(); // draw everything on the canvas that you specified in your code
    canvas.addDelay(5); //  add a short 5 ms delay
}
```

## **How to contribute**
This code base can certainly be optimized, and more features can be added.  Feel free to make changes or improvements.  Please rebuild the jar file when you make changes, so any teachers or students that download the project have access to it.  Keep in mind that this project is intended for use by students, so please make sure it is easy and straight forward to use.

