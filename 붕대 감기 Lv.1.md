```java

class Solution {
    public int solution(int[] bandage, int health, int[][] attacks) { // bandage : 시전 시간, 초당 회복량, 추가 회복량

        int total = health;
        int attackIdx = 0;
        int success = 0;

for (int i = 1; i <= attacks[attacks.length-1][0]; i++){ // 1초부터 마지막 공격 받은 시간까지 반복
            if(i != attacks[attackIdx][0]){             // 공격을 받지 않았을 경우
                    total += bandage[1];                // 1초당 회복량만큼 체력에 더해주기
                    success++;                          // 연속 성공횟수 증가
                if (success == bandage[0]){             // 연속 성공횟수와 시전 시간이 같아질 경우
                    total += bandage[2];                // 추가 회복량만큼 체력에 더해주기
                    success = 0;                        // 그 이후에는 연속 성공이 초기화
                }
                if (total > health)
                    total = health;                      // 최대 체력을 넘어서지 않도록
            }else{                                       // 공격을 받았을 경우
                      success = 0;                       // 연속 성공 횟수 초기화
                      total -= attacks[attackIdx][1];    // 체력 감소
                      attackIdx++;                       // 공격 횟수 증가
            if (total <= 0) return -1;                   // 체력이 0 이하면 -1 리턴
            }
      }
        return total;
}
}
```
![image](https://github.com/yezini/programmers/assets/85025359/7cd5ab4c-ffdb-4a11-a942-2cc4019de8c0)

