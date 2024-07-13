```java
import java.util.*;

class Solution {
    public int solution(int k, int[] tangerine) {  // k 고르는 귤의 개수, tangerine 귤의 크기를 담은 배열
        int sum = 0; // 고를 귤의 개수
        int cnt = 0; // 최솟값

        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>(); // 귤의 크기를 담은 배열의 정수를 HashMap의 키 값
        for(int t : tangerine) {  // 1, 3, 2, 5, 4, 5, 2, 3
            map.put(t, map.getOrDefault(t, 0) + 1);  // {1:1, 2:2, 3:2, 4:1, 5:2} (귤의 크기 : 귤의 개수)
        }

        ArrayList<Integer> list = new ArrayList<>(map.values()); // 귤의 개수에 해당하는 value를 배열로 변환

        Collections.sort(list, Collections.reverseOrder()); // list를 내림차순으로 정렬 2 2 2 1 1
        for (int s : list) { // 2 2 2 1 1
            if (sum + s >= k) { // k=6
                cnt++; // cnt = 3
                break;
            } else {
                sum += s; // sum = 2 4
                cnt++; // cnt = 1 2
            }
        }
        return cnt; // 3
        }
}
```
