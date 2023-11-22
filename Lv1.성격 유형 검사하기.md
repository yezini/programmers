```java
import java.util.*;

class Solution {
    public String solution(String[] survey, int[] choices) {
        String answer = "";
        String [][] test ={{"R","T"},{"C","F"},{"J","M"},{"A","N"}}; //성격 유형
        int score[] = {3,2,1,0,1,2,3};                                // 비동의 , 모르겠음, 동의 순서대로 점수
        
        Map<String, Integer> map = new HashMap<>();            //성격 유형과 점수를 key와 value로 저장
        
        for(int i=0; i<survey.length; i++){              //총 5번 반복 
            String s = survey[i];                       //"AN"
            if(choices[i] < 4){                         //choices의 값이 1,2,3,4 일떄는 비동의, 모르겠음
                
                String t = String.valueOf(s.charAt(0)); //비동의에 해당하기 때문에 "CF" 중 앞 문자만 해당 = C
                map.put(t,map.getOrDefault(t,0)+score[choices[i]-1]);                  
                
            }else if(choices[i] > 4){                   //choices의 값이 5,6,7 일때는 동의
                
                String t = String.valueOf(s.charAt(1)); //동의에 해당하기 때문에 "AN" 중 뒤 문자만 해당 = N
                map.put(t,map.getOrDefault(t,0)+score[choices[i]-1]);  
                
            }    
        }
            for(int i=0; i<4; i++){
                if(map.getOrDefault(test[i][0],0) >= map.getOrDefault(test[i][1],0)){  //점수가 더 큰 값 비교하여 answer에 성격유형 담기 
                    answer += test[i][0];
                }else answer += test[i][1];
            }
            return answer; 

    }
}
