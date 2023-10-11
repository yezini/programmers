``` java
class Solution {
// 이진 변환의 횟수와 변환 과정에서 제거된 모든 0의 개수를 각각 배열
    public int[] solution(String s) {
        int[] answer = new int[2]; //이진 변환 횟수와 제거된 0의 개수 
//  s가 1이 될 때까지 계속해서 s에 이진 변환
//  만약 01110 일 경우, 먼저 0의 개수는 2개 / 0의 제거후 길이 3 / 이진 변환하면 11
//                     11의 0의 개수는 0개 / 0의 제거후 길이 2 / 이진 변환하면 10
//                     10의 0의 개수는 1개 / 0의 제거후 길이 1 / 결과 1
while(s.length() > 1) {
      


}

        return answer;
    }
}
