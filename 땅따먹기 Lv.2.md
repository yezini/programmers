```java
import java.util.*;
class Solution {
    int solution(int[][] land) {
        //위에서 부터 값을 체크하여 마지막에 가장 큰 값 출력되도록 
        for(int i =1;i<land.length;i++){
            //같은 열을 반복할 수 없으니까 0번째를 제외하고 최대값 구해서 더하기  
              land[i][0] += Math.max(Math.max(land[i-1][1],land[i-1][2]),land[i-1][3]);
              land[i][1] += Math.max(Math.max(land[i-1][0],land[i-1][2]),land[i-1][3]);
              land[i][2] += Math.max(Math.max(land[i-1][0],land[i-1][1]),land[i-1][3]);
              land[i][3] += Math.max(Math.max(land[i-1][0],land[i-1][1]),land[i-1][2]);
                
        }   
            int [] answer = land[land.length-1];
            Arrays.sort(answer); 
            return answer[answer.length-1];
    }
}
