```java
class Solution {
    public int solution(int number, int limit, int power) {  //만약 number 10, limit 3, power 2일 경우
        // 약수의 개수 1 2 2 3 2 4 2 4 3 4   
        int[] count = new int[number + 1];                  //크기가 11인 count 배열 생성
        for (int i = 1; i <= number; i++) {                  
            for (int j = 1; j <= number / i; j++) {        //약수의 개수 구하기
                // i=1, j=1 ~ j=10, count[1]=1 count[2]=1 ... count[10]=1
                // i=2, j=1 ~ j=5, count[2]=1 count[4]=1 count[6]=1 ... count[10]=1
                // i=3, j=1 ~ j=3, count[1]=1 count[6]=1 count[9]=1
                // i=4, j=1 ~ j=2, count[4]=1 count[8]=1 
                count[i * j]++;                          //약수의 개수를 count 배열에 담기   
            }
        }
        int answer = 0;
        for (int i = 1; i <= number; i++) {
            if (count[i] > limit) {                      //limit 보다 크면 power를 더하고
                answer += power;
            } else {                                    //limit 보다 작으면 자신의 배열의 값을 더하기 
                answer += count[i];
            }
        }
        return answer;
    }
}
