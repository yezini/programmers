```java
class Solution {
    public int[] solution(int n, long left, long right) {
        int[] answer = new int[(int)(right-left+1)]; //크기만큼만 탐색
        int index=0;
        
        for(long i=left;i<=right;i++){ //Math.max(행,열) + 1 
        long low = i/n;   //행 (몫)
        long col = i%n;   //열 (나머지)
        answer[index++]=Math.max((int)low,(int)col)+1;
            
        }
        
        return answer;
    }
}
