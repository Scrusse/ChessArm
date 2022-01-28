# Chess Robot Arm
### Table of Contents

* [CAD Section](#CAD-Section)
* [Chess Pieces](#Chess-Pieces)
* [Coding Section](#Coding-Section)

## Cad Section

### Chess Pieces

In this project, I didn't want to just brush by the designing aspect and rip some chess piece designs off the internet. I wanted to actually try to design my own. Not only would it make it more legit, but it would be fun and give me good practice with Onshape. So that is exactly what I did. Using the revolve tool, I could create a 2d sketch of a chess piece cut in half. All I would have to do is revolve it around the center construction line and the sketch would become a chess piece. There were some complications with the parts of the special pieces where I would have to create a seperate sektch on a seperate plane to remove sections from parts of pieces. Another complication was the knight. Of course, the knight isn't a symmetrical piece and couldn't use the revolve tool. My solution? Create a base using the revolve tool and then extrude a flat sketch onto it. Did it look good? Not exactly, but I think the unicorn horn made up for it.

The image below is a pawn, the first piece I made. I made this completely from scratch using no reference images. 


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
