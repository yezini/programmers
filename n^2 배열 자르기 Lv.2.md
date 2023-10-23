```java
class Solution {
    public int[] solution(int n, long left, long right) {
        int[] answer = new int[(int)(right-left+1)];
        int index=0;
        
        for(long i=left;i<=right;i++){
        long low = i/n;   //행 
        long col = i%n;   //열
        answer[index++]=Math.max((int)low,(int)col)+1;
            
        }
        
        return answer;
    }
}
