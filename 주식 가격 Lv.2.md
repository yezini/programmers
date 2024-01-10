```java
class Solution {
    public int[] solution(int[] prices) {
        int[] answer = new int[prices.length];
        // 가격이 떨어지지 않는 기간 = 현재 시간의 주식 가격보다 높거나 같은 주식 가격의 기간 
        
        for(int i=0; i<prices.length-1;i++){      // 마지막은 무조건 0일 수 밖에 없으니깐 4번만 반복
            for(int j=i+1; j<prices.length; j++){ // i가 0일 때 j는 1, 2, 3, 4 총 4번 반복
                   answer[i]++;                   // 처음 1초일 때는 항상 1보다 가격이 크기 때문에 answer 증가(=4)  
                                            // 2초일 때도 3,4,5초에 해당하는 값이 전부 2보다 크기 때문에 answer 증가(=3)
                if(prices[i] > prices[j]){  // 3초일 때는 5초에 해당하는 값만 해당하기 때문에 answer 한번 증가(=1)
                    break;
                }
            }
        }
        return answer;
    }
}
