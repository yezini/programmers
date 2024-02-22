```java
class Solution {
    public int solution(String[] board) {
         int succes=1,fail=0;
        
        char[][] b = new char[board.length][board.length];
        int o_cnt = 0;
        int x_cnt = 0;
        
        for(int i=0;i<board.length;i++){
            for(int j=0;j<board.length;j++){
                char c = board[i].charAt(j);
                if(c=='O')       o_cnt ++;
                else if(c=='X')  x_cnt ++;
                b[i][j]= c;
            }
        }
        if(x_cnt > o_cnt || o_cnt-x_cnt > 1  ) return fail;             // O가 선방, X가 후방이기 때문에 X의 개수가 O의 개수보다 많을 수 없음
                                                                        // O와 X의 개수 차이가 1보다 클 수 없음(번갈아가면서 게임) 
                                                                            
    }
}

```
