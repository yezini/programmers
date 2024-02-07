```java
import java.lang.Math;
 
class Solution {
    public int[] solution(String[] wallpaper) { // ["..........", ".....#....", "......##..", "...##.....", "....#....."]
        int[] answer = new int[4];
        answer[0] = wallpaper.length;        // 최대 5
        answer[1] = wallpaper[0].length();   // 최대 10
        answer[2] = 0;                       // 최소 0
        answer[3] = 0;                       // 최소 0
        
        for (int i = 0; i < wallpaper.length; i++) { //5번 반복하면서 
            String[] s = wallpaper[i].split(""); 
            for (int j = 0; j < s.length; j++) {
                if ("#".equals(s[j])) { // 파일이 있는 칸은 #에 해당  
                    answer[0] = Math.min(answer[0], i); 
                    answer[1] = Math.min(answer[1], j);
                    answer[2] = Math.max(answer[2], i);
                    answer[3] = Math.max(answer[3], j);
                }
            }
        }
        
        answer[2] += 1; // 점의 좌표이기 때문에 마지막에 1을 더하여 리턴 
        answer[3] += 1; // 점의 좌표이기 때문에 마지막에 1을 더하여 리턴 
        
        return answer;
    }
}
```
