```java
class Solution
{
    public int solution(int [][]board)
    {
        int answer = 0;
        int[][] newBoard = new int[board.length+1][board[0].length+1];

        // 새로운 배열 생성
        for(int i=0; i<board.length; i++)
            for(int j=0; j<board[i].length; j++)
                newBoard[i+1][j+1] = board[i][j];
                 // 행이 1이거나 열이 1이면 예외 경우 발생하기 때문에 +1 (배열 [0][n] 값과 [n][0]의 값을 모두 0으로 채워줌으로써)
        int max = 0;

        for(int i=1; i<newBoard.length; i++){
            for(int j=1; j<newBoard[i].length; j++){
                /* 사각형의 우측하단 꼭짓점을 기준으로 현재 값이 1인경우 좌, 상, 왼쪽 위 대각선 체크
                 *( 모두 1인경우 정사각형을 만들 수 있음 )
                */
                if(newBoard[i][j] == 1){
                    int left = newBoard[i-1][j];    // 좌측 값
                    int up = newBoard[i][j-1];      // 상단 값
                    int left_up = newBoard[i-1][j-1];// 왼쪽 위 대각선 값
                    int min = Math.min(left, Math.min(up, left_up));
                    newBoard[i][j] = min+1;    // 최솟값 + 1을 설정
                    max = Math.max(max, min+1);
                }
            }
        }
        answer = max * max;
        return answer;
    }
}


```

