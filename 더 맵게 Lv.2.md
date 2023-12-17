```java
import java.util.*;

class Solution {
    public int solution(int[] scoville, int K) {
        int answer = 0;
        int a,b;
        // 가장 최상위에 있는 데이터가 가장 맵지 않은 음식으로 이 값이 k보다 크면 모든 음식이 k보다 큰 것 
        // 우선수위 큐 생성 (최소힙으로 만들어주기 때문에 사용)
        PriorityQueue<Integer> queue = new PriorityQueue<>();
        
        for(int i=0; i<scoville.length; i++){       // 6번 반복하며
            queue.add(scoville[i]);                 // queue에 값 할당 
        }
        
        while(queue.peek() < K){    // 가장 최상위에 있는 값이 7보다 작을때만 반복
            if(queue.size() < 2){    // 스코빌 길이는 2 이상 이여야 하므로 -1 리턴 
                return -1;
            }else{
                a = queue.poll();    // 맨 앞 값 빼기, 1 / 3
                b = queue.poll();    //               2 / 5
                
                a = a + (b*2) ;       // 5              / 13
                queue.offer(a);       // 3 5 9 10 12     / 9 10 12 13
                answer +=1;
            }
            
        }
        
        return answer;
    }
}
