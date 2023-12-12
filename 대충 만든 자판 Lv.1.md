```java
import java.util.*;
class Solution {
    public int[] solution(String[] keymap, String[] targets) {
        // A B A C D => 1 2 3 4 5
        // A B C D => 1 2 4 5
        // A B C D E F => 1 1 2 5 3 4  
        
        int[] answer = new int[targets.length];
        HashMap<Character,Integer> map = new HashMap<>();  // 해당 문자와 인덱스로 맵 생성
        
        for(int i=0; i<keymap.length; i++){                 // 2번 반복
            for(int j=0; j<keymap[i].length(); j++){          // 5번 반복 
                char c = keymap[i].charAt(j);               // 문자열에서 하나의 문자만 반환 ('A','B','A','C','D')
                if(map.containsKey(c)){                     // 해시맵의 키, c가 존재할 때
                    int index = map.get(c);                 // 해시맵의 값, 인덱스에 해당하는 값 
                    map.put(c,Math.min(j+1,index));         // 알파벳의 최소로 누를 수 있는 인덱스를 저장           
                }
                else{
                    map.put(c,j+1);                         // (A,1) (B,2) (C,4) (D,5)
                }
            }
        }
        for(int i=0; i<targets.length; i++){    
            String target = targets[i];                     // ABCD
            int count = 0;                                  // 총 횟수 카운트
            boolean n = true;                               // 존재하지 않는 문자일 경우
            for(char test :target.toCharArray()){           // ['A','B','C','D']
                if(map.containsKey(test)){                  // 해시맵에 타겟 존재 여부를 키로 판단 
                    count += map.get(test);                 // 키로 해당 값 즉, 인덱스 가져오기 
                }
                else{
                    n = false;                              // 존재하지 않는 문자일 경우
                    break;
                }
            }
            answer[i] = n == false ? -1 : count;
        }
        
        return answer;
    }
}
