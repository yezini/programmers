```java

import java.util.*;

class Solution {
    public boolean solution(String[] phoneBook) {//접두어를 포함하고 있으면 false 리턴, 포함하지 않고 있으면 true 리턴
        Map<String, Integer> map = new HashMap<>(); //전화번호를 키 값으로 하여 HashMap 생성

        for (int i = 0; i < phoneBook.length; i++)
            map.put(phoneBook[i], i); //모든 전화번호를 map에 넣기 (119,0) (97674223,1) (1195524421,2)

        for (int i = 0; i < phoneBook.length; i++)
            for (int j = 0; j < phoneBook[i].length(); j++)
                if (map.containsKey(phoneBook[i].substring(0, j)))//모든 전화번호의 substring으로 map에 존재하는지 확인
                    return false;
            return true;
    }
}

```

