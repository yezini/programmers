```java
import java.util.*;
public class Solution {
    boolean solution(String s) {
        boolean answer = true;
        
        Stack<Character> stack=new Stack<>();//Character로 선언해야함 
        
        for(int i=0;i<s.length();i++){
            if(s.charAt(i)=='('){//charAt은 문자열 중에서 한 글자만 선택해서 char 타입으로 반환함 
                stack.push('(');
            }
           else{
                if(stack.isEmpty()){//)가 들어갈 자리인데 비어있으면 false 
                    return false;
                }else{
                    stack.pop();
                }  
                }
          
        }
        answer=stack.isEmpty()?true:false;

        return answer;
    }
}
```
