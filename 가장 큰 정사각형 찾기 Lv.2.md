```java
class Solution
{
    public int solution(int [][]board)
    {
        int[][] dp = new int[board.length][board[0].length];
        
        int answer = 0;
        for(int i = 0; i < board.length; i++) {
            for(int j = 0; j < board[i].length; j++) {
                int value = board[i][j];
                if(value == 0) continue;
                
                dp[i][j] = (i == 0 || j == 0) 
                    ? value
                    : Math.min(Math.min(dp[i-1][j], dp[i][j-1]), dp[i-1][j-1]) + 1;
                
                answer = Math.max(answer, dp[i][j]);
            }
        }
        

        return answer * answer;
    }
}


```

