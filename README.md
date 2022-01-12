# ChessArm
A robot arm that can move chess pieces to a desired location on a chess board.


code as of january 12th



        int cols=12;
        int rows=8;
        int[][] board = new int[cols][rows];
        //establish pshapes
        void setup() {
        size(1201, 801);
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
            circle(i*100+50, j*100+50, 50);
            fill(255);
          }
          stroke(0);
          line((i+1)*100, 0, (i+1)*100, 800);
          line(0, (j+1)*100, 1200, (j+1)*100);
        }
      }
      }
      void draw() {
      //begin moving pieces to starting positions
      if (mousePressed) {
        stroke(60, 190, 120);
        fill(60, 190, 210);
      }
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

