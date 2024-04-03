```java
class Solution {
    public int answer; // 최대 던전 수
    public boolean[] y; // 해당 던전을 참여했는지 여부 

    public int solution(int k, int[][] dungeons) { //k는 현재 피로도, 최소 필요 피로도와 소모 피로도
        
        y = new boolean[dungeons.length]; // dungeons 배열의 길이만큼 해당 던전 참여 여부 배열 선언

        // dfs 메서드 호출
        dfs(0, k, dungeons);

        // 결과 반환
        return answer;
    }

    public void dfs(int depth, int k, int[][] dungeons) { // depth는 현재까지 탐색한 던전 수 
        for (int i = 0; i < dungeons.length; i++) {
            
            if (!y[i] && dungeons[i][0] <= k) { // 참여하지 않은 던전이며 k가 최소 필요 피로도보다는 크거나 같아야함 
                y[i] = true; // 참여 처리
                dfs(depth + 1, k - dungeons[i][1], dungeons); // 깊이는 1 증가하며 다음 던전을 수행하기 위해 재귀 호출
                // 현재 피로도에서 탐험한 던전의 소모 피로도를 빼주기 
                
                y[i] = false; // 참여 초기화
            }
        }
        // 반복문이 끝나면 answer 변수에 최대 던전 수를 저장하여 리턴 
        answer = Math.max(answer, depth);
    }
}

```

![image](https://github.com/yezini/programmers/assets/85025359/9e81edd2-1b3f-41c1-9a73-6b6aa9135a00)
