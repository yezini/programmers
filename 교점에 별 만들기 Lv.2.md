```java
import java.util.*;

class Gps {   // 좌표 (생성자 및 setter 생성)
    long x;
    long y;

    Gps(long x, long y){
        this.x = x;
        this.y = y;
    }

    void setX(long x){
        this.x = x;
    }

    void setY(long y){
        this.y = y;
    }
    
}
// Ax + By + E = 0      -> 2x-y+4=0
// Cx + Dy + F = 0      -> -2x-y+4=0
// line :  [[2, -1, 4], [-2, -1, 4], [0, -1, 1], [5, -8, -12], [5, 8, 12]]

class Solution {
    public String[] solution(int[][] line) {
        List<Gps> list = new ArrayList<>(); // 교점을 저장할 좌표 리스트 생성

        for(int i = 0; i < line.length - 1; i++){   // 모든 경우의 수 반복
            for(int j = i + 1; j < line.length; j++){

                long a = line[i][0], b = line[i][1], e = line[i][2],  // a=2 b=-1 c=4
                     c = line[j][0], d = line[j][1], f = line[j][2];  // c=5 d=-8 f=-12

                if((a * d - b * c) != 0){ // ad- bc = 0인 경우 두 직선은 평행 또는 일치
                    double x = (double) (b * f - e * d) / (a * d - b * c);      // 교점의 좌표 -4
                    double y = (double) (e * c - a * f) / (a * d - b * c);      // 교점의 좌표 -4

                    if(x % 1 == 0 && y % 1 == 0){                      // 정수인 경우에만 저장하도록
                    list.add(new Gps((long)x, (long)y));    // (4, 1), (4, -4), (-4, -4), (-4, 1), (0, 4)   
                    }
                }
            }
        }

        Gps min = new Gps(Long.MAX_VALUE, Long.MAX_VALUE);         // 교점의 최소, 최대값 찾기 
        Gps max = new Gps(Long.MIN_VALUE, Long.MIN_VALUE);          

        for(Gps c : list){    // (4, 1), (4, -4), (-4, -4), (-4, 1), (0, 4)  
            long cx = c.x;             
            long cy = c.y;    

            if(cx < min.x){  // 값들 비교하면서 최소,최대값 설정 
              min.setX(cx);
            }

            if(cy < min.y){
                min.setY(cy);
            }

            if(cx > max.x){
                max.setX(cx);
            }

            if(cy > max.y){
                max.setY(cy);
            }
        }

        int w = (int)(max.x - min.x + 1); // 격자판 가로   
        int h = (int)(max.y - min.y + 1); // 격자판 세로  

        char[][] arr = new char[h][w];  // 격자판 배열 생성 -> [y값][x값]

        for(int i = 0; i < h; i++){
            for(int j = 0; j < w; j++){
                arr[i][j] = '.';        // . 찍기
            }
        }

        for(Gps c : list){      // (4, 1), (4, -4), (-4, -4), (-4, 1), (0, 4)
            arr[(int)(max.y - c.y)][(int)(c.x - min.x)] = '*'; // 교점에 * 찍기 arr[3][8] 
        }

        String[] answer = new String[h];

        for(int i = 0; i < answer.length; i++){
            answer[i] = new String(arr[i]);  // 문자열로 변환하여 저장
        }

        return answer;
    }
}

```

![image](https://github.com/yezini/programmers/assets/85025359/2c56c74c-dc8e-4c94-84e3-4db1d8c940b5)
