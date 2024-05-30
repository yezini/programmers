```java
/* 풀이 참고하여 미완성 */
// 11011 11011 00000 11011 11011 (3구역 포함여부로 나눠서 처리)
class Solution {
    int answer;
    public int solution(int n, long l, long r) {  //n=3 (총 5^(n-1)개)(1의 개수 16, 0의 개수 9 ), 시작과 끝 범위 
        answer = 0;
        long areaLength = 1;
        int countOne =1;
        while(n>1){
            areaLength *= 5L;      //5배수로 전체 개수가 늘어나며 1의 개수는 4^(n-1)개 
            countOne *= 4;         //4배수 
            n--;
        }
        dfs(areaLength, countOne, l,r);  //재귀함수 호출 

        return answer;
    }
    private void dfs(long areaLength, int countOne, long start, long end){  //시작 4, 끝 17
        if(areaLength == 1L){
            long c = end - start + 1;
            if(c >= 3 || end ==3 || start == 3){
                c--;
            }
            answer +=c;
            return;
        }
												    //시작 4, 끝 17

        long startArea = start / areaLength;           //몫으로 시작 지점 구역 지정(Long 타입) 
        if(start % areaLength > 0){  
            startArea++;
        }
        long endArea = end/areaLength;             //끝 지점 구역 
        if(end % areaLength > 0) {
            endArea++;
        }

        if(endArea > startArea){			//같은 구역에 속해있는게 아니라면 (전체 5구역 중 2구역, 4구역에 포함된 범위라면 )
            long includArea = endArea - startArea - 1L;
            if(startArea%5 < 3 && ((endArea)%5 >3 || endArea%5 == 0)){  // 3구역을 포함하고 있으면 
                includArea--;
            }
            answer += (includArea*countOne);

            if(startArea != 3) {                                //구역을 두 개로 나눠서 (시작지점이 3구역이 아닌경우)
                dfs(areaLength / 5, countOne / 4, start, startArea * areaLength);     //시작부터 시작구역 끝부분 까지 
            }
            if(endArea != 3){					//(끝지점이 3구역이 아닌경우)
                dfs(areaLength/5 ,countOne/4, (endArea-1)*areaLength+1 , end);     //끝구역 시작부분부터 끝까지
            }
        }
        else{
            if(startArea == 3) return;                  //중간지역이 존재하지 않는다면 한번 더 재귀 
            dfs(areaLength/5 ,countOne/4, start, end);  //지정된 범위시작부터 끝까지 재귀 
        }

    }

}
```
