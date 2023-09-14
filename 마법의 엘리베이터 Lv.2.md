```java

class Solution {
    public int solution(int storey) {
        int answer = 0;

      // 6부터 9까지는 10으로 만들기, 1부터 4까지는 0으로 만들기
      // 5일 경우에는 앞 숫자까지 판단 -> 예를들어 50 이상 100에 가까운 숫자는 숫자를 올리고 0 이상 50 미만에 가까운 숫자는 숫자를 내린다.

    while (storey > 0) {
            int remainder = storey % 10;  // 나머지
            storey /= 10;                 // 몫 

            // 나머지가 5인 경우
            if(remainder == 5){
                  if(storey % 10 >= 5 ){
                      answer += (10 - remainder);
                      storey ++;
              }else{
                      answer += remainder; 
            }

            }

           // 나머지가 5보다 크면 10에서 빼는게 유리 (87 -> -87 = -10 * 9 + 1 * 3 )
            else if (remainder > 5) {
                answer += (10 - remainder);
                storey++;
            }
            // 나머지가 5보다 작으면 더하는게 유리 (13 -> -13 = -10 * 1 + (-1) * 3 )
            else {
                answer += remainder;
            }

        return answer;
    }
}
