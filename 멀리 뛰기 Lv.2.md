```java
// 1 2 3 4 5 6    :  1 2 3 5 8 13
// 피보나치수열(재귀호출) f(n)= f(n-1) + f(n-2)

class Solution {
    public long solution(int n) {
        long arr []= new long[2001];
      
	    arr[1]=1;
	    arr[2]=2;     //arr[3]=3, arr[4]=5, arr[5]=8
	 
	    for(int i=3; i<=2000; i++) {  //2000 이하인 정수 
		    arr[i] = (arr[i-1]+arr[i-2]) % 1234567;		//피보나치수열	 
	    }		 
	        return arr[n];
        
    }
}

```
