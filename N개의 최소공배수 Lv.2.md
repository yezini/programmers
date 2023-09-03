```java
import java.util.*;
class Solution {
     public static int gcd(int a , int b){
           int x= Math.max(a,b);
            int y=Math.min(a,b);//만약 6와 8이라면 x=8, y=6
            
            while(x%y!=0){
        int r=x%y;
                x=y;
                y=r;
            }
            return y;
        }
    
    public int solution(int[] arr) {
//         int answer = 1;
//      int small=arr[0];   
//         for(int i=0;i<arr.length;i++){
//             if(arr[i]%small==0){
//                 int s=arr[i]/small;
//                 answer=answer*s;
         
//             }else{
//                 answer=answer*arr[i];
//             }
//         }
        
//         return answer;
        int answer=0;
        //원소가 한 개인 경우 바로 출력
        if(arr.length==1) return arr[0];
        
        //원소가 두개인 경우
      int g=  gcd(arr[0],arr[1]);//두 원소의 최대공약수를 구하는 함수에 해당 
        answer=(arr[0]*arr[1])/g;
        
        //원소가 3개 이상인 경우
        if(arr.length>2){
            for(int i=2;i<arr.length;i++){
                //만약 7 14 21인 경우 7과 14에 대한 최소공배수를 구한 뒤 
                //최소공배수와 21의 최소공배수를 배열의 끝까지 반복
                g=gcd(answer,arr[i]);//최대 공약수 구하기
                answer=(answer*arr[i])/g;
            } 
        }
        return answer;
       
          
        
    }
}
```
