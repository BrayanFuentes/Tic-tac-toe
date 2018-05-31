# Tic-tac-toe
import java.util.Arrays;
public class gameBoard
{
    private char[][] gameBoard;
    private boolean gameOnGoing = true;                                                                                                                                                                            
    public gameBoard()
    {
        gameBoard = new char[3][3];
        
        for(int row = 0; row < gameBoard.length; row++)
        {
           Arrays.fill(gameBoard[row], ' ');
            
        }
    }
    
    public void displayBoard()
    {
        for(int row = 0; row < gameBoard.length; row++)
        {
            for(int col = 0; col < gameBoard[0].length; col++)
            {
                System.out.print("\t" + gameBoard[row][col]);
                if(col == 0 || col == 1)
                {
                    System.out.print("|"); 
                }
            }
            if(row == 0 || row == 1)
            {
                System.out.print("\n---------------------------\n"); 
            }
        }
        System.out.println();
    }
    
    public boolean activeGame()
    {
        return gameOnGoing;
    }
    
    public boolean submitMove(char move, int row, int col)
    {
        if(row >= 0 && row <= 2 && col >= 0 &&  col <= 2)
        {
            if( gameBoard[row][col] != ' ')
            {
                return false;
            }
            else
            {
                gameBoard[row][col] = move;
                return true;
            }
        }
        else
        {
            return false;
        }
    }
    
    public boolean isWinner()
    {
        for(int row =0; row< gameBoard.length; row++)
        {
            if (gameBoard[row][0] == gameBoard[row][1] && gameBoard[row][1]== gameBoard[row][2] && gameBoard[row][0] !=' ')
            {
                System.out.print(gameBoard[row][0] + " is the winner");
                gameOnGoing = false;
            }
         }
        
        for (int col = 0; col < gameBoard[0].length; col++)
        {
            if (gameBoard[0][col] == gameBoard[1][col] && gameBoard[1][col]== gameBoard[2][col] && gameBoard[0][col] !=' ')
            {
                System.out.print(gameBoard[0][col] + " is the winner");
                gameOnGoing = false;
            }
        }
        
        if(gameBoard[0][0] == gameBoard[1][1] && gameBoard[1][1] == gameBoard[2][2] && gameBoard[0][0] != ' ')
        {
            System.out.print(gameBoard[0][0] + " is the winner");
            gameOnGoing = false;
        }
        
        if(gameBoard[2][0] == gameBoard[1][1] && gameBoard[1][1] == gameBoard[0][2] && gameBoard[0][2] != ' ')
        {
            System.out.print(gameBoard[2][0] + " is the winner");
            gameOnGoing = false;
        }
        
        return false;
    }
    
    
    public boolean isEmpty(int row, int col)
    {
        if(gameBoard[row-1][col-1] == ' ')
        {
            return true;
        }
        else 
        {
            System.out.print("That position is already taken/ \n");
            return false;
        }
    }
    
    public boolean isCat()
    {
        for(int row =0; row< gameBoard.length; row++)
        {
            if (gameBoard[row][0] != gameBoard[row][1] || gameBoard[row][1] != gameBoard[row][2])
            {
                System.out.print("Cat's game");
                gameOnGoing = false;
            }
         }
        for (int col = 0; col < gameBoard[0].length; col++)
        {
            if (gameBoard[0][col] != gameBoard[1][col] || gameBoard[1][col]!= gameBoard[2][col])
            {
                System.out.print("Cat's game");
                gameOnGoing = false;;
            }
        }
        
        if(gameBoard[0][0] != gameBoard[1][1] || gameBoard[1][1] != gameBoard[2][2])
        {
            System.out.print("Cat's game");
            gameOnGoing = false;
        }
        
        if(gameBoard[2][0] != gameBoard[1][1] || gameBoard[1][1] != gameBoard[0][2])
          {  
              System.out.print("Cat's game");
              gameOnGoing = false;
        }
        
        return false;
    }
    
    public boolean isMoveValid(int row, int col)
    {
        if(row > 3 || row < 1 )
        {
            return true;
        }
        else if(col  > 3 || col < 1 )
        {
            return true;
        }
        else if(!isEmpty(row,col))
        {
            return true;
        }
        else
        {
        return false;
        }
    }
}
