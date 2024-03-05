```java
class Solution {
    public int[] solution(String[] park, String[] routes) {
        int parkHeight =park.length;//공원 세로
        int parkWeight =park[0].length();//공원 가로
        int robotHeight =0;//로봇 세로
        int robotWeight =0;//로봇 가로

        String[][] parkpark = new String[parkHeight][parkWeight];//2차원 배열로 공원
        for(int i=0; i<parkHeight;i++){
            String[] parks = park[i].split("");
                for(int j=0; j<parkWeight;j++){
                  parkpark[i][j]=parks[j];
                }
        }
        for(int i=0;i<parkHeight;i++){
            for(int j=0;j<parkWeight;j++){
                if(parkpark[i][j].equals("S")){//S에 해당하는 로봇 위치를 변수에 담아기
                    robotHeight=i;
                    robotWeight=j;
                    break;
                }
            }
        }
        for(int i=0; i<routes.length;i++){
            String[] spl = routes[i].split(" ");//방향과 이동 횟수 split으로 분리
            int count = Integer.parseInt(spl[1]);//string으로 형 변환했기 때문에 이동 횟수 int 로 형 변환
            boolean go = true;
            //X는 장애물, break를 걸면 해당 반복문만 탈출함으로 뒤의 실행을 막기 위해서 go라는 boolean 타입을 true로 선언
            //장애물을 만나게되면 go를 false로 하여 false 일 경우에는 switch 문 통과하게끔

            switch(spl[0]){
                case "N"://북쪽으로 이동
                    if(robotHeight-count<0){
                           break;     //로봇 위치보다 이동 횟수가 더 크면 H좌표가 줄어들어서 0보다 작아질 수 있는 오류
                    }
                    for(int n=1;n<=count;n++){
                        if(parkpark[robotHeight-n][robotWeight].equals("X")){ //robotHeight-n 만큼 북쪽으로 이동, 만약 X를 만나게되면 go를 false로 하여 switch문 통과
                            go = false;
                    }
                    }
                    if(go==false){
                           break;
                    }
                    robotHeight-=count;//모든 예외경우가 아닐 경우 로봇 위치 count만큼 이동
                    break;
                case "S"://남쪽으로 이동하여 H좌표가 커져 공원 크기보다 커질 수 있는 오류
                    if(robotHeight+count>=parkHeight){//count만큼 남쪽으로 이동 시 공원보다 커지게 되면 break
                            break;
                    }
                    for(int n=1;n<=count;n++){
                        if(parkpark[robotHeight+n][robotWeight].equals("X")){//robotHeight+n 만큼 남쪽으로 이동, 만약 X를 만나게되면 go를 false로 하여 switch문 통과
                            go = false;
                    }
                    }
                    if(go==false){
                            break;
                    }
                    robotHeight+=count;//모든 예외경우가 아닐 경우 로봇 위치 count만큼 이동
                    break;
                case "W"://서쪽으로 이동하여 W좌표가 줄어들어서 0보다 작아질 수 있는 오류
                    if(robotWeight-count<0){
                            break;
                    }
                     for(int n=1;n<=count;n++){
                        if(parkpark[robotHeight][robotWeight-n].equals("X")){//robotWeight-n 만큼 서쪽으로 이동, 만약 X를 만나게되면 go를 false로 하여 switch문 통과
                            go = false;
                    }
                    }
                    if(go==false){
                            break;
                    }
                    robotWeight-=count;//count만큼 서쪽으로 이동
                    break;
                case "E"://동쪽으로 이동하여 W좌표가 커져 공원의 크기보다 커질 수 있는 오류
                    if(robotWeight+count>=parkWeight){
                            break;
                    }
                    for(int n=1;n<=count;n++){
                        if(parkpark[robotHeight][robotWeight+n].equals("X")){//robotWeight+n 만큼 동쪽으로 이동, 만약 X를 만나게되면 go를 false로 하여 switch문 통과
                            go = false;
                    }
                    }
                    if(go==false){
                            break;
                    }
                    robotWeight+=count;//모든 예외경우가 아닐 경우 로봇 위치 count만큼 이동
                    break;
            }
        }
        int[] answer = new int[2]; //명령이 끝난 후 로봇이 놓인 세로와 가로의 좌표 위치
        answer[0] = robotHeight;
        answer[1] = robotWeight;
        return answer;
    }
}


```
![image](https://github.com/yezini/programmers/assets/85025359/c9af2a70-b34b-4214-8b9d-4193c254c75c)
