```java

class Solution {
    // 변수 접근을 위한 전역 변수
    static int numberOfArea;
    static int maxSizeOfOneArea;
    
    // 한 영역의 수를 저장하는 변수
    static int temp_cnt = 0;
    
    static int[] dx = {-1,1,0,0}; // 상,하 탐색을 위한 배열
    static int[] dy = {0,0,-1,1}; // 좌,우 탐색을 위한 배열
    
    // dfs
    public static void dfs(int x,int y, int[][] picture, boolean[][] check){
        
        if(check[x][y]) return; // 방문한 적 있는 좌표이면 DFS 종료
        
        check[x][y] = true;  // 처음 방문 시 방문 처리
        temp_cnt++; // 영역 수 증가 
        
        for(int i =0;i<4;i++){ // 좌표에서 상,하,좌,우 탐색
            int nx = x + dx[i];
            int ny = y + dy[i];
            
            // 좌표가 picture 배열의 범위를 벗어나면 continue
            if(nx<0 || nx>=picture.length || ny<0 || ny>=picture[0].length) 
                continue;
            
            // 현재 좌표의 색과 상,하,좌,우 좌표의 색이 같고 방문한적 없는 상,하,좌,우 좌표일 때 재귀호출
            if(picture[x][y] == picture[nx][ny] && !check[nx][ny]){                
                dfs(nx,ny,picture,check);
            }            
        }        
    }
    
    public int[] solution(int m, int n, int[][] picture) {
        numberOfArea =0; // 초기화 
        maxSizeOfOneArea=0;
        
        int[] answer = new int[2];
        answer[0] = numberOfArea;
        answer[1] = maxSizeOfOneArea;
        
        boolean[][] check = new boolean[m][n]; // DFS시 방문 여부를 체크 할 배열
        
        // picture 배열 탐색
        for(int i =0;i<m;i++){
            for(int j=0;j<n;j++){
               
                if(picture[i][j] != 0 && !check[i][j]){  // 원소가 0이 아니고 방문한 적이 없다면
                    numberOfArea++; // 영역의 수 1 증가 
                    dfs(i,j,picture,check); // dfs 탐색 
                }
                // 탐색이 모두 끝났다면 조건에 따라 최대 영역의 수 변경
                if(temp_cnt > maxSizeOfOneArea) 
                    maxSizeOfOneArea = temp_cnt;
                    temp_cnt = 0; // 영역 다시 초기화
            }
        }
        // 각 값을 answer 배열에 담아주기 
        answer[0] = numberOfArea;
        answer[1] = maxSizeOfOneArea;
        
        return answer;
    }
}


```
