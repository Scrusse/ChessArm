# Chess Robot Arm
### Table of Contents

* [CAD Section](#CAD-Section)
* [Chess Pieces](#Chess-Pieces)
* [Robot Arm & Box](#Robot-Arm-&-Box)
* [Rack & Pinion](#Rack-&-Pinion)
* [Coding Section](#Coding-Section)

## Cad Section

### Chess Pieces

In this project, I didn't want to just brush by the designing aspect and rip some chess piece designs off the internet. I wanted to actually try to design my own. Not only would it make it more legit, but it would be fun and give me good practice with Onshape. So that is exactly what I did. Using the revolve tool, I could create a 2d sketch of a chess piece cut in half. All I would have to do is revolve it around the center construction line and the sketch would become a chess piece. There were some complications with the parts of the special pieces where I would have to create a seperate sketch on a seperate plane to remove sections from parts of pieces. Another complication was the knight. Of course, the knight isn't a symmetrical piece and couldn't use the revolve tool. My solution? Create a base using the revolve tool and then extrude a flat sketch onto it. Did it look good? Not exactly, but I think the unicorn horn made up for it.


The images below are of the pawn, the first piece I made. I made this completely from scratch using no reference images. Splines, while they are the worst lines in existance, were my only choice here. I just messed around with some ovals and splines and got what is shown here.

This is the bishop. It uses the same base as the pawn and with a stretched out body. The top is pointed and has another smaller tip on it's head. There is a cut through the head that is made by creating a sketch seperate from the original one and removing material from that one section in a straight line (as opposed to a revolved one).

This is the knight. It looks pretty scuffed because of the fact that I couldn't revolve it so I had to use a reference image. I think that it would be far worse without the fillets, but it still could look better.

The rook is one of my favorites. Originally, the three indents seen on the top, middle, and base weren't there and, personally, I think they somehow made it way better. Note to self: things look better with more random details (sometimes). The top was pretty straight forward. I created a sketch on the very top flat surface of the cup shape and made two lines pointing at different angles coming from the center of the circle. After extruding that, I did a circular feature pattern. Fillets make everything looks nicer, so that was the final touch.

The third piece I made, the queen, was no doubt the hardest. While the main sketch design was all freestyle, the bumps on the crown were very challenging. I had to create a new plane that is the same angle as the crown, and then make a cut through the crown at the same angle it is pointing. After that I just repeated what I did with the rook and did a circular feature pattern. Not only did I make a pattern for the crown, but I decided to make one for the tip of the head. Because it was rounded, I had to make an offset plane that was right above the top of the queen and then make a sketch that fits what I needed it to. After that, extruded it to cut through the whole top and no more and then did a circular mattern once again.

For the king, I think I had a really good idea. The plan was to make the crown be hollow in the middle with bar shapes surrounding it. I had to first, create a hole in the sketch before revolving it. This way, it wouldn't look hollow when first revolving it, but I would be able to cut out rectangles from the outside and reveal the hollowed inside. So next, I had to make another plane with a specific angle that was facing the the crown. I made a sketch that fit the crown and then extruded it and created a pattern around. For the plus sign on top of the crown, I couldnt include it in the revolve. So, what I had to do was just extrude it serparately. 

### Robot Arm & Box

### Rack & Pinion Designing

The gear has probably given me the most problems so far. Getting a gear to fit properly on a rack. The rack has to fit perfectly on the teeth of the gear, otherwise it could cause too much wobbling. The gear was simpler than I had first anticepated because I could just simply use a custom onshape feature that allows me to create one with just information about the dimensions. Though, before I figured that out, I had spent a good week trying to find a proper gear generator online. It didn't go well. After I made the gear, the last thing to do was make the rack. Easier said than done. Long story short, I had to watch a tutorial on how to create a rack and pinion in onshape and copy the exact dimensions. The problem was that I wanted it to be a different size than it was in the tutorial. What I did was I created a variable for every dimension on one section of the rack and related each one to the diameter the gear's pitch circle diameter (example: variable #a = #PitchCircleDiameter/1.6). This way I could change the variable for the gear's diameter (which is what I wanted to change) and at the same time change the size of the rack flawlessly. I think it ended up working out, but it was a lot of work for just a rack and pinion.

This is the gear and rack together.

The sketch for the rack is shown below.

These are all of the variables I used for the rack.


## Coding Section

Written by @Ashanks70

<details>
<summary>Code</summary>
<br>
        <details>
        <summary>January 12th</summary>
                
        //establish array
        PImage wpawn;
        int cols=12;
        int rows=8;
        int[][] board = new int[cols][rows];
        //establish pshapes
        void setup() {
          size(1201, 801);
          wpawn=loadImage("Pawn.png");
          background(#CAA472);
          stroke(163, 50, 50);
          line(0, 0, 1200, 0);
          line(0, 1198, 1200, 1198);
          line(0, 0, 0, 1200);
          line(1200, 0, 1200, 1200);
          for (int i = 0; i < cols; i++) {
            for (int j = 0; j < rows; j++) {
              if (j%2==0 && i%2==1) {
                fill(#964B00);
                stroke(0);
                square((i*100), (j*100), 100);
                fill(255);
              }
              if (j%2==1 && i%2==0) {
                fill(#964B00);
                stroke(0);
                square((i*100), (j*100), 100);
                fill(255);
              }
              if (i<=1 || i >= 10) {
                if (i <=1) {
                  stroke(0);
                  fill(0);
                }
                if (i>=10) {
                  stroke(255);
                  fill(255);
                }
              stroke(0);
              line((i+1)*100, 0, (i+1)*100, 800);
              line(0, (j+1)*100, 1200, (j+1)*100);
            }
          }
         }
        }
        void draw() {
          background(#CAA472);
          stroke(#CAA472);
          rect(0,0,600,400);
          line(0, 0, 1200, 0);
          line(0, 1198, 1200, 1198);
          line(0, 0, 0, 1200);
          line(1200, 0, 1200, 1200);
          for (int i = 0; i < cols; i++) {
            for (int j = 0; j < rows; j++) {
              if (j%2==0 && i%2==1) {
                fill(#964B00);
                stroke(0);
                square((i*100), (j*100), 100);
                fill(255);
              }
              if (j%2==1 && i%2==0) {
                fill(#964B00);
                stroke(0);
                square((i*100), (j*100), 100);
                fill(255);
              }
              if (i<=1 || i >= 10) {
                if (i <=1) {
                  stroke(0);
                  fill(0);
                }
                if (i>=10) {
                  stroke(255);
                  fill(255);
                }
                circle(i*100+50, j*100+50, 50);
                fill(255);
              }
              stroke(0);
              line((i+1)*100, 0, (i+1)*100, 800);
              line(0, (j+1)*100, 1200, (j+1)*100);
            }
          }
        for (int j = 0; j < rows; j++){
        image(wpawn,1021,j*100);

        }

        }
          //begin moving pieces to starting positions

        void mousePressed(){
        circle(mouseX,mouseY,pmouseX);

        }
        void keyPressed() {
          if (key=='r') {

            //reset pieces
          }
        }

        //obtain first click position(mouse)
        //obtain second position(pmouse)
        //check isvalidmove
        //if it works move on board and relay to arduino

        //isValidMove(piece type)
        //if piece == rook...
        //if move works then return true
        //else return false)

</details>
