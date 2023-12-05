```java
class Solution {
    int count = 0;
    public int solution(int[] numbers, int target) {
        //numbers = [4,1,2,1]  target = 4
        int answer = 0;
        dfs(numbers, 0,  target, 0); // 깊이 우선 탐색 
        answer = count;                       // 4의 개수를 카운트  
        return answer;
        
    }
    
    public void dfs(int[] numbers, int depth, int target, int result){
        if(depth == numbers.length){            // 깊이가 4이고 해당 결과값이 target이 되면 count 증가
            if(target == result){
                count++;
            }
            return;
        }
        int a = result + numbers[depth];        // 0 + 4
        int b = result - numbers[depth];        // 0 - 4
        
        dfs(numbers, depth+1, target, a);
        dfs(numbers, depth+1, target, b);       //깊이는 계속 증가
        
    }
    
}
