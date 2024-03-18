```java
class Solution {
    public int solution(int[] ingredient) {
        int answer = 0;
        StringBuilder sb = new StringBuilder();

for(int i=0; i < ingredient.length; i++) {
            sb.append(ingredient[i]);

            if(sb.length()>3) {                             // 빵 야채 고기 빵이 완성되었을 때 햄버거인지 확인
                if(sb.charAt(sb.length()-1) == '1' &&       // 맨위의 빵에 해당(1)
                   sb.charAt(sb.length()-2) == '3' &&       // 고기(3)
                   sb.charAt(sb.length()-3) == '2' &&       // 야채(2)
                   sb.charAt(sb.length()-4) == '1') {       // 맨 아래의 빵에 해당(1)
                    answer++;

              sb = new StringBuilder(sb.substring(0, sb.length()-4));      // 햄버거 하나 완성 시 완성된 햄버거 재료는 삭제 후 다시 위의 반복문 반복
                                                                           // [2, 1, 1, 2, 3, 1, 2, 3, 1]  -> [2, 1]
                    }         
                }
            }
        return answer;
    }
}

```
