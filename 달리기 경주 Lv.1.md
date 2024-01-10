```java
import java.util.*;

class Solution {
    public String[] solution(String[] players, String[] callings) {
             
        Map<String, Integer> map = new HashMap<>();     // 선수 이름과 해당 인덱스로 맵 생성
        
        for(int i=0; i<players.length;i++){             // 선수들만큼 반복하며 맵에 값 할당 
            //"mumu", "soe", "poe", "kai", "mine"
            // 0       1       2      3      4
            map.put(players[i],i);                      
        }
        
        for(String player : callings){                  // 해설진이 부른 이름이 담긴 배열 callings만큼 반복
            // player : "kai", "kai", "mine", "mine"
            int rank = map.get(player);                 // kai 라는 선수 이름의 인덱스, rank = 3
            String beforePlayer = players[rank-1];      // 앞서가던 선수
            
            // players 배열 갱신
            players[rank-1] = player;
            players[rank] =  beforePlayer;
            
            // map 갱신
            map.put(player,rank-1);
            map.put(beforePlayer,rank);
            
        }
        
        return players;
    }
}
