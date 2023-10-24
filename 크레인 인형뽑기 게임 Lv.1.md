```java
class Solution {
    public int solution(int[][] board, int[] moves) {
        int answer = 0;
        Stack<Integer> stack = new Stack<>();    

        for(int i = 0; i<moves.length;i++){                   //8번 반복 (1 5 3 5 1 2 1 4)
            for(int j = 0; j<board.length;j++){               //2차원 배열 board만큼 반복 (j = 0,1,2,3,4 )
                    if(board[j][moves[i]-1] != 0)  {          //인형이 있을 경우에만 
                                  if(!stack.isEmpty() && stack.peek() == board[j][moves[i]-1]) { //스택이 비어있지 않고 스택의 최상위 값과 뽑은 값이 일치할 때 인형 사라짐 
                                        stack.pop();          //인형 사라짐
                                        answer +=2;           //2개 카운트
                                  }else
                                      stack.push(board[j][moves[i]-1]);     //스택에 해당 값 넣기
                                      board[j][moves[i]-1] = 0;             //넣은 공간은 다시 0으로 만들어줘야함
                                      break;
                                  }    
                                          }
                                              }
        return answer;
    }
}
