import java.util.*;

public class App  {
    public static void main(String[] args) throws Exception {
        char winner = ' ';
        char[] TicTacToe = new char[9];
        for (int i = 0; i < TicTacToe.length; i++) {
            TicTacToe[i] = winner;
        }
        

        Scanner move = new Scanner(System.in); // For Moves
        Scanner play = new Scanner(System.in); // Decisions prior to game
        Random robot = new Random(); // For Robot Player
        
       ArrayList<Integer> moves = new ArrayList<>(); 
       for (int i = 1; i < 10; i++ ) {
            moves.add(i);
        }        
        
        // For robot to select moves from & prevent picking taken spots
         //Playing against robot. Remove from array so robot doesn't keep picking used spots.
      
         int Player1Wins = 0;
        int Player2Wins = 0; // Person and Robot are both considered player 2.
        int Draws = 0;

      System.out.println("Welcome to Tic-Tac-Toe!");
      System.out.println("The rules are as follows." + "\n");
      PrintOriginalBoard();
      System.out.println(" " );
      System.out.println("The number in each board is where your move (X) will go!");
      System.out.println("Would you like to play? Yes/No");

      String decision = play.next();
      int game;

      while (decision.equalsIgnoreCase("yes")) {
        System.out.println("Enter 1 for Player v. Player or 2 for Player v. Robot ");
        game = play.nextInt();
        System.out.println("The game has started! Enter a move between 1-9!");
        PrintOngoingBoard(TicTacToe);
       
       
        int player1Move;
        boolean validity1 = true;
        int robotMove;
        boolean robotValidity = true;

      if (game == 1 ) {
       
         while(!GameOver(TicTacToe)) {
            do {
                System.out.println("Player 1 Move...");
                player1Move = play.nextInt();
                validity1 = Player1Setter(TicTacToe, player1Move);
                if (!validity1) {
                    System.out.println("Invalid Move. Try Again.");
                } else {
                PrintOngoingBoard(TicTacToe);
             } 
               } while(!validity1);

               if(GameOver(TicTacToe)) {
                break;

               }
// ---------------------------------------------------------------------------------
            int player2Move;
            boolean validity2 = true;
            do {
                System.out.println("Player 2 Move...");                
                player2Move = play.nextInt();
                validity2 = Player2Setter(TicTacToe, player2Move);
                if (!validity2) {
                   System.out.println("Invalid Move. Try Again");
                }  else {
                PrintOngoingBoard(TicTacToe);
             } 
              } while(!validity2);

              if(GameOver(TicTacToe)) {
                break; 
              } // Check if there is a winner so both player don't have to enter move before winner is determined

          }
        }
//-----------------------------------------------------------------------------------
            if (game == 2) {
                while(!GameOver(TicTacToe)) {
                    do {
                        System.out.println("Player 1 Move...");
                        player1Move = play.nextInt();
                        validity1 = Player1Setter(TicTacToe, player1Move);
                        if (!validity1) {
                            System.out.println("Invalid Move. Try Again.");
                        } else {
                        PrintOngoingBoard(TicTacToe);
                        moves.remove(Integer.valueOf(player1Move));
                     }
                    }while(!validity1);

                    if (GameOver(TicTacToe)) {
                        break;
                    }
                
                
                do {
                    if((VictoryDecider(TicTacToe) == 'O')) {
                        break;
                    }
                    System.out.println("RoboTac is Thinking...");
                    int picked = robot.nextInt(moves.size());
                    robotMove = moves.get(picked);
                    moves.remove(Integer.valueOf(robotMove));
                    robotValidity = Player2Setter(TicTacToe, robotMove);
                    if (!robotValidity) {
                        continue;
                    } else {
                    PrintOngoingBoard(TicTacToe);
                    moves.remove(Integer.valueOf(robotMove));
                }
              }while(!robotValidity); 

                if(GameOver(TicTacToe)) {
                    break;
                }
           }
        }
            
            
        

//-----------------------------------------------------------------      
    
        char result = VictoryDecider(TicTacToe);
        if (result == 'X') {
            System.out.println("Player 1 Wins!");
            PrintOngoingBoard(TicTacToe);
            Player1Wins++;
        } else if(result == 'O') {
            System.out.println("Player 2 Wins!");
            PrintOngoingBoard(TicTacToe);
            Player2Wins++;
        } else if (checkIfFull(TicTacToe)) {
            PrintOngoingBoard(TicTacToe);
            System.out.println("It's a Draw!");
            Draws++;
        } // Prints out winner and counts wins for win info at the end

        System.out.println("Would you like to play again? Yes/No");
        decision = play.next();
      

         Arrays.fill(TicTacToe, ' ');
       
          for (int i = 1; i < 10; i++ ) {
          moves.add(i);
             }        // Reset board and ArrayList 
    }

//----------------------------------------------------------------------------
    System.out.println("Thanks for Playing!");
    System.out.println("Player 1 Wins: " + Player1Wins);
    System.out.println("Player 2 Wins: " + Player2Wins);
    System.out.println("Draws: " + Draws);

    
move.close();
play.close();
}


//------------------------------------------------------------------------------
    
       public static char Equality(char one, char two, char three) {
        if (Character.toUpperCase(one) == Character.toUpperCase(two) 
        && Character.toUpperCase(two) == Character.toUpperCase(three) 
        && Character.toUpperCase(one)  == Character.toUpperCase(three) ) {
            return Character.toUpperCase(one);
        }
        return ' ';
     }

       public static char VictoryDecider(char[] TicTacToe) {
        if(Equality(TicTacToe[0], TicTacToe[1], TicTacToe[2]) == 'X' ||
        Equality(TicTacToe[3], TicTacToe[4], TicTacToe[5]) == 'X' ||
        Equality(TicTacToe[6], TicTacToe[7], TicTacToe[8]) == 'X' || 
        Equality(TicTacToe[0], TicTacToe[4], TicTacToe[8]) == 'X' ||
        Equality(TicTacToe[0], TicTacToe[3], TicTacToe[6]) == 'X' ||
        Equality(TicTacToe[1], TicTacToe[4], TicTacToe[7]) == 'X' ||
        Equality(TicTacToe[2], TicTacToe[5], TicTacToe[8]) == 'X' ||
        Equality(TicTacToe[2], TicTacToe[4], TicTacToe[6]) == 'X') {
            return 'X';
        }
        if (Equality(TicTacToe[0], TicTacToe[1], TicTacToe[2]) == 'O' ||
        Equality(TicTacToe[3], TicTacToe[4], TicTacToe[5]) == 'O' ||
        Equality(TicTacToe[6], TicTacToe[7], TicTacToe[8]) == 'O' || 
        Equality(TicTacToe[0], TicTacToe[4], TicTacToe[8]) == 'O' ||
        Equality(TicTacToe[0], TicTacToe[3], TicTacToe[6]) == 'O' ||
        Equality(TicTacToe[1], TicTacToe[4], TicTacToe[7]) == 'O' ||
        Equality(TicTacToe[2], TicTacToe[5], TicTacToe[8]) == 'O' ||
        Equality(TicTacToe[2], TicTacToe[4], TicTacToe[6]) == 'O') {
            return 'O';
         } 
         return ' ';
     }

    

     public static void PrintOriginalBoard() {
        System.out.println("| 1 | 2 | 3 |");
        System.out.println("-------------");
        System.out.println("| 4 | 5 | 6 |");
        System.out.println("-------------");
        System.out.println("| 7 | 8 | 9 |");
     }
    

     public static void PrintOngoingBoard(char[] TicTacToe) {
        System.out.println("|   " + TicTacToe[0] + "   |   " + TicTacToe[1] +  "   |   " + TicTacToe[2] + "   |");
        System.out.println("-------------");
        System.out.println("|   " + TicTacToe[3] + "   |   " + TicTacToe[4] +  "   |   " + TicTacToe[5] + "   |");

        System.out.println("-------------");
        System.out.println("|   " + TicTacToe[6] + "   |   " + TicTacToe[7] +  "   |   " + TicTacToe[8] + "   |");

     }
    
          

          public static boolean GameOver(char[] TicTacToe) {
            if(VictoryDecider(TicTacToe) == 'X' || VictoryDecider(TicTacToe) == 'O' || checkIfFull(TicTacToe)) {
                return true;
            }
            return false;
          }
          public static boolean Player1Setter(char[] TicTacToe, int position ) {
            if (TicTacToe[position - 1] != ' ' || position < 1 || position > 9) {
                return false;
            } else {
                TicTacToe[position - 1] = 'X';
                return true;
            }
      }
      public static boolean Player2Setter(char[] TicTacToe, int position) {
        if (TicTacToe[position - 1] != ' ' || position < 1 || position > 9) {
            return false;
        } else {
            TicTacToe[position - 1] = 'O';
            return true;
        }
    }

  public static boolean checkIfFull(char[] TicTacToe) {
    for (int i = 0; i < TicTacToe.length; i++) {
        if (TicTacToe[i] != 'X' && TicTacToe[i] != 'O' ) {
            return false;
        } 
    }
        return true; 
}
}


