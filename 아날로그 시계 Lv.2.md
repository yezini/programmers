```java

// 초침 1초에 360/60 = 6도씩 움직임, 만약 1분이면 360도

// 분침 1초에 360/3600 = 0.1도씩 움직임, 만약 1분이면 6도

// 시침 1초에 1/120 도씩 움직임, 만약 1분이면 0.5도, 만약 1시간이면 30도

// 만약 시간 03:33:45
//
// 초침 = 45 x 6
// 분침 = (33 x 6) + (45 x 0.1)
// 시침 = (3 x 30) + (33 x 0.5) + (45 x 1/120))
//
// h:m:s 로 나타내면
//
// 초침 = 6s
// 분침 = 6m + 0.1s
// 시침 = (h % 12) x 30 + 0.5m + (1/120) s   (0부터 23까지 시간이며 시침은 12시간 마다 360도를 돌기 때문에 % 12를 해줘야함)

// 초침 분침 시침 각도를 구한 후 일반식으로 작성해서 문제를 풀려고 했는데... 잘 모르겠어서 다른 분 풀이를 보고 이해하는 정도까지만 했습니다....



import java.util.*;

class Solution {

      static class Time{

            int h, m, s ;

            Time(int h, int m, int s){
            this.h = h;
            this.m = m;
            this.s = s;
        }

        Time(int seconds){    // 초로 변환된 시간으로 Time 클래스 접근하도록 생성자 정의
            this.h = seconds / 3600;
            this.m = (seconds % 3600) / 60;
            this.s = (seconds % 3600) % 60;
        }

        int toSeconds(){    // 모든 시간을 초로 변환
            return h * 3600 + m * 60 + s;
        }


        List<Double> getDegree(){     // 각도를 계산해서 List 형태로 반환
            Double hDegree = (h % 12) * 30d + m*0.5d + s * (1/120d);
            Double mDegree = m * 6d + s * (0.1d);
            Double sDegree = s * 6d;

            return List.of(hDegree,mDegree,sDegree);
        }
      }

    public int solution(int h1, int m1, int s1, int h2, int m2, int s2) {
        int answer = 0;

        int start = new Time(h1,m1,s1).toSeconds();  // 시작 시간과 종료 시간을 초 단위로 변경
        int end = new Time(h2,m2,s2).toSeconds();

        for(int i = start; i <end; i++){      // 시작 시간부터 1초씩 올려가며 계산하며 마지막 초는 포함되면 안됨

            List<Double> cnt = new Time(i).getDegree();           	// 시간이 i초일 때 각도 계산
            List<Double> next = new Time(i+1).getDegree();

            boolean hMatch = hourMatch(cnt,next);
            boolean mMatch = minuteMatch(cnt,next);


            if(hMatch && mMatch){  // 초침이 분침과 시침과 겹침이 발생

                if(Double.compare(next.get(0),next.get(1)) == 0) answer++;  // 시침과 분침의 각도가 같다면 +1

                else answer +=2;
            }

            else if(hMatch || mMatch) answer++;  // 둘 중 하나라도 겹치면 +1
        }

        // 위 로직은 시작시간에 대한 검사를 X

        if(start == 0 || start == 43200) answer++;          // 그래서 0시 또는 12시에 시작한다면 한번 겹치고 시작하는 것이기 때문에 +1

        return answer;
    }


    boolean hourMatch(List<Double> cnt, List<Double> next){  // 시침가 초침의 겹침
        if(Double.compare(cnt.get(0),cnt.get(2)) > 0 && Double.compare(next.get(0),next.get(2)) <= 0){
            return true;
        }

        if(Double.compare(cnt.get(2),354d) == 0 && Double.compare(cnt.get(0),354d) > 0){    // 초침이 354도에서 0도로 넘어갈 때 예외
            return true;
        }
        return false;
    }

    boolean minuteMatch(List<Double> cnt, List<Double> next){   // 분침과 초침의 겹침
        if(Double.compare(cnt.get(1),cnt.get(2)) > 0 && Double.compare(next.get(1),next.get(2)) <= 0){
            return true;
        }

        if(Double.compare(cnt.get(2),354d) == 0 && Double.compare(cnt.get(1),354d) > 0){  // 초침이 354도에서 0도로 넘어갈 때 예외
            return true;
        }
        return false;
    }
}

```
