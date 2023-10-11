```java

import java.util.*;
class Solution {
    public int solution(int[] elements) {
 //원형 수열로 끝자리에서 처음 자리로 다시 이어지는 경우로 인해 배열을 2배로 추가로 늘리기
        int[] newElements = new int[elements.length*2];
        
        for(int i=0;i<elements.length;i++){
          newElements[i+elements.length]= newElements[i]=elements[i];
        //newElements[0]==newElements[5]
        }
        //중복 허용하지 않는 set 함수 변수 선언 
        Set<Integer> set= new HashSet<>();
        for(int i=1;i<=elements.length;i++){
            for(int j=0;j<elements.length;j++){
                set.add(Arrays.stream(newElements,j,j+i).sum());
                //newElements의 리스트 값에서 j 인덱스 시작, 끝-1의 값들의 합 
            }
        }
        return set.size();//set은 중복되지 않았으며 set의 개수를 리턴 
    }
}
