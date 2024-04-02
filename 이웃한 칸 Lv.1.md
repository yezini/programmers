```java

class Solution {
    public int solution(String[][] board, int h, int w) { 
        int count = 0; //같은 색으로 색칠된 칸의 개수 저장할 변수 
        int n = board.length; //board의 길이 저장 
        
        int[] dh = new int[] {0,1,-1,0}; //변화량을 저장할 변수에 해당 
        int[] dw = new int[] {1,0,0,-1};
        
        for(int i = 0 ; i < dh.length ; i++){
            int h_check = h + dh[i]; //체크할 칸의 h의 좌표를 나타내는 변수 
            int w_check = w + dw[i];
            if(h_check >= 0 && h_check < n && w_check >= 0 && w_check < n ){ //4-2에 해당 
                if(board[h][w].equals(board[h_check][w_check])){ //4-2-a에 해당 
                    count++;
                }
            }
        }
        return count;
    }
}

```

![image](https://github.com/yezini/programmers/assets/85025359/fbf40b27-e505-4867-8745-c97986af6f9b)
