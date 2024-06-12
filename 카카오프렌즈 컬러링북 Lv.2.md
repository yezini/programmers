```java

class Solution {
    public int[] solution(int m, int n, int[][] picture) {
        // 변수 접근을 위한 전역 변수들  
        static int numberOfArea = 0;
        static int maxSizeOfOneArea = 0;

        // 한 영역의 수를 저장하는 변수
        static int temp_cnt = 0;
        
        // 좌표에서의 상,하,좌,우 탐색을 위한 배열
        static int[] dx = {-1,1,0,0};
        static int[] dy = {0,0,-1,1};
    
        // DFS 메소드
        public static void dfs(int x,int y, int[][] picture, boolean[][] check){
        
                  if(check[x][y]) return; // 방문한 적 있는 좌표라면 DFS 종료
        
                  check[x][y] = true; // 처음 방문 시 방문 처리
                  temp_cnt++ ; // 영역의 수 증가
        
                  // 좌표에서 상,하,좌,우 탐색
                  for(int i =0; i<4; i++){
                                int nx = x + dx[i];
                                int ny = y + dy[i];
            
            if(nx<0 || nx>=picture.length || ny<0 || ny>=picture[0].length) continue; // picture 배열의 범위를 벗어나면 continue
          
            if(picture[x][y] == picture[nx][ny] && !check[nx][ny]){ //  현 좌표의 색 == 상,하,좌,우 좌표의 색 && 방문한적 없는 상,하,좌,우 좌표라면               
                dfs(nx,ny,picture,check); // DFS를 위한 재귀호출
            }            
        }        
    }
    
    public int[] solution(int m, int n, int[][] picture) {
    
        numberOfArea =0;  // 초기화
        maxSizeOfOneArea=0;
        int[] answer = new int[2];
        answer[0] = numberOfArea;
        answer[1] = maxSizeOfOneArea;
        
        // DFS시 방문여부를 체크 할 배열
        boolean[][] check = new boolean[m][n];
        
        // 주어진 picture 배열을 탐색
        for(int i =0;i<m;i++){
            for(int j=0;j<n;j++){
                if(picture[i][j] != 0 && !check[i][j]){ // 원소가 0이 아니고, 방문한 적이 없다면 영역의 수가 1개 증가하며 DFS 탐색 수행
                    numberOfArea++;
                    dfs(i,j,picture,check);
                }
                // 한 영역의 탐색이 모두 끝났다면, 조건에 따라 최대 영역의 수를 변경
                if(temp_cnt > maxSizeOfOneArea) maxSizeOfOneArea = temp_cnt;
                temp_cnt = 0; // 한 영역의 수는 다시 초기화
            }
        }
         
        answer[0] = numberOfArea; // 각 값을 answer 배열에 담기
        answer[1] = maxSizeOfOneArea;
        
        return answer;
      }
      }
    }
}


```
