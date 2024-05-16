
```java


import java.util.*;

class Solution {
    public int[] rotateNums(int[][] square, int[][] queries){// queries : [[2,2,5,4],[3,3,6,6],[5,1,6,3]]
        int[] answer = new int[queries.length];
        int minimalsIdx=0;

        for(int[] query : queries){ // 각 행렬을 인덱스로 사용하기 위해서 각 요소마다 -1
            int x1 = query[0]-1; // 2 -> 1
            int y1 = query[1]-1; // 2 -> 1
            int x2 = query[2]-1; // 5 -> 4
            int y2 = query[3]-1  // 4 -> 3
            int firstNum = square[x1][y2]; // 처음으로 밀려서 덮어씌어진 숫자 10을 저장하기 위한 변수
            int min = firstNum;

            /* 시계방향으로 처리하기 위해서 순서를 시계와 반대방향으로 처리 */
            // 상단에서 숫자를 우로 이동
            for(int i=y2-1; i>=y1; i--){ // 2
                min = Math.min(min, square[x1][i]); // 가장 작은 값으로 덮어씌우기 때문에 덮어씌울 때마다 min 함수 사용
                square[x1][i+1] = square[x1][i];
            }

            // 좌측에서 숫자를 위로 이동
            for(int i=x1+1; i<=x2; i++){
                min = Math.min(min, square[i][y1]);
                square[i-1][y1] = square[i][y1];
            }

            // 하단에서 숫자를 좌로 이동
            for(int i=y1+1; i<=y2; i++){
                min = Math.min(min, square[x2][i]);
                square[x2][i-1] = square[x2][i];
            }

            // 우측에서 숫자를 아래로 이동
            for(int i=x2-1; i>=x1; i--){
                min = Math.min(min, square[i][y2]);
                square[i+1][y2] = square[i][y2];
            }

            square[x1+1][y2] = firstNum;  // 처음 저장한 숫자 10을 회전이 다 끝난 후 해당 위치에 넣기
            answer[minimalsIdx] = min;
            minimalsIdx++;
        }

        return answer;
    }

    public int[][] initSquare(int rows, int columns){
        int[][] square = new int[rows][columns];
        int value = 1;
        for(int i=0; i<rows; i++){
            for(int j=0; j<columns; j++){
                square[i][j] = value;
                value++;
            }
        }

        return square;
    }

    public int[] solution(int rows, int columns, int[][] queries) { // 6, 6, [[2,2,5,4],[3,3,6,6],[5,1,6,3]]
        int[] answer = {};
        int[][] square = initSquare(rows, columns);
        return rotateNums(square, queries);
    }
}
```
