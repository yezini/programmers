```java
import java.util.*;

class Solution {
    public int solution(int[][] targets) {
        int answer = 0;
        
        Arrays.sort(targets, (o1, o2) -> {
            return o1[1] - o2[1];   // 끝점으로 오름차순 정렬 
        });
        
        int end = targets[0][1];    // [1,4]의 끝점인 4 저장 
        answer++; // 첫 번째로 만들어지는 요격 시스템
        
        for(int[] target : targets){ 
            if(target[0] >= end){ 
//1 >= 4 (X), 4 >= 4 (O) end에 5 저장, 3 >= 5(X), 4 >= 5(X), 5 >= 5 (O) end에 12 저장, 11 >= 12(X), 10 >= 12 (X)
                end = target[1];
                answer++; 
            }
        }
        
        return answer;
    }
}
```

<img width="301" alt="image" src="https://github.com/yezini/programmers/assets/85025359/c520e6c0-a665-4357-aa13-cbe1f1a1039b">
