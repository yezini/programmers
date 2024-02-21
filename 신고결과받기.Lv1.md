```java
import java.util.*;
class Solution {
    public int[] solution(String[] id_list, String[] report, int k) {
        int[] answer = new int[id_list.length];
        
        Map<String, HashSet<String>> map = new HashMap<>();
        Map<String, Integer> ind = new HashMap<>();
        
        for(int i=0;i<id_list.length;i++){
            String name = id_list[i];
            map.put(name, new HashSet<>());
            ind.put(name,i);
        }
        for(String s:report){
            String[] str = s.split(" ");
            String A = str[0];
            String B = str[1];
            map.get(B).add(A);
        }
        for(int i=0;i<id_list.length;i++){
            HashSet<String> m = map.get(id_list[i]);
            if(m.size()>=k){
                for(String name : m){
                    answer[ind.get(name)]++;
                }
            }
        }
        return answer;
    }
}
```
