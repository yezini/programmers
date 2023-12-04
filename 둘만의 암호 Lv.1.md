```java
import java.util.*;

class Solution {
    public String solution(String s, String skip, int index) {
        // abcdefghijklmnopqrstuvwxyz 총 26개 
        String answer = "";
        // "aukks" 중 a에서 5만큼 뒤에 있는 알파벳은 f지만 skip을 제외하고서는 h에 해당 
        for(int i=0; i<s.length(); i++){     // 5번 반복
            char c = s.chartAt(i);           // 문자열 s에서 하나 문자만 뽑기 즉, a에 해당
            
            int count = 1;
            while(count <= index){    
                ++c;                        
                if(c > 'z')                 // 만약 z보다 크게 되면 다시 a로 돌아감 
                    c-=26;
                if(skip.contains(c+"")) continue;
                else count++;
                    
            }
            answer+= c;
        }
    
        return answer;
    }
}
