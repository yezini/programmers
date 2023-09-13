```java
import java.util.Arrays;
class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
       // 여벌옷이 있으면서 잃어버린 학생과 여벌옷이 없으면서 잃어버린 학생을 나눠서 생각
       // lost[]과 reverse[] 배열을 순차적으로 비교하기 위하여 정렬

        Arrays.sort(lost);
        Arrays.sort(reserve);

       // 결과값인 전체 학생 수는 n명에서 체육복을 잃어버린 학생의 수를 뺀 값
        int answer = n - lost.length;

      // 여벌옷이 있으면서 잃어버린 학생의 경우
for (int i=0; i<lost.length;i++){
  for(int j=0; j<reserve.length; j++){
      if(lost[i]==reserve[j]){
        answer ++; //여벌옷으로 체육복 사용
        lost[i] = -1;//잃어버린 옷에서 경우의 수 지우기
        reserve[j] = -1;//여벌옷에서 경우의 수 지우기
        break;
    }
  }
}

    // 여벌옷이 없으면서 잃어버린 학생의 경우
for (int i=0; i<lost.length;i++){
  for(int j=0; j<reserve.length; j++){
      // 앞번호의 학생이나 바로 뒷번호의 학생에게만 체육복을 빌려줄 수 있다
       if((reserve[j]==lost[i]-1) || (reserve[j]==lost[i]+1)   ){
          answer ++;
           reserve[j] = -1;
           break;
}

  }
}
       return answer;
    }
}
