```java
class Solution { 
    public int[] solution(int brown, int yellow) {  
        //갈색 10, 노랑 2일 때 전체 카펫 3 * 4 = 12
        //(3+4-2) * 2 = 10, 전체 카펫 12 - 10(갈색) = 2(노랑)
        //(8+6-2) * 2 = 24, 전체 카펫 48 - 24(갈색) = 24(노랑)
        
        //갈색 테두리 안에 노랑이 들어가려면 가로, 세로 최소 3 
        for(int width = 3; width <= 5000; width++){
            for(int height = 3; height <= width; height++){
                
                int brown1 = (width + height - 2) * 2;  // 10
                int yellow1 = width * height - brown1; // 전체 12 - 10 = 2
                
                if(brown == brown1 && yellow == yellow1){
                    return new int[] {width, height};// 카펫의 가로, 세로 리턴 
                }
            }
        }
       return null;
    }
}
```

![image](https://github.com/yezini/programmers/assets/85025359/40cb47b1-00dc-463a-9b49-c5f13efc974c)
