```java
// 가입자를 최대한 늘리는게 우선이며 2번째 목표가 판매액을 높이는 것 
class Solution {
    
int sign=0;
int earn=0;
    public int[] solution(int[][] users, int[] emoticons) {
        // users 사용자 n명의 구매 기준을 담은 2차원 정수 배열 [[40, 10000], [25, 10000]] 
        // (40% 이상의 할인이 있는 이모티콘을 모두 구매, 10000원 이상의 돈을 사용하여 구매하면 구매를 모두 취소하고 가입)
        // emoticons 이모티콘 정가 [7000, 9000]
        
        int[] answer = new int [2]; // 결과적으로 가입 수와 판매액 
        
        int[] arr =new int[emoticons.length]; // 크기가 2인 배열 arr 
        
        comb(arr,0,users,emoticons); // 10% ,20%, 30% ,40% 할인되는 분기를 완전탐색 
        
        answer[0]=sign; // 최대 가입 수  
        answer[1]=earn; // 최대 판매액 
        
        return answer; 
    }
    
    public void comb(int[] arr,int start,int[][] users,int[] emoticons){
        
        if(start==arr.length){  // 모든 할인율이 적용되었다면 최대 가입 수와 최대 판매액 계산
            calculate(arr,users,emoticons); 
            return;
        }
        
        for(int i=10;i<=40;i+=10){ // 4번의 할인율로 계산 
            arr[start]=i; // arr[0] = 10 ,arr[1] = 20
            comb(arr,start+1,users,emoticons); // comb(10,1,users,emotions), comb(20,2,users,emotions)
        }
        
    }
    
    public void calculate(int[] arr,int[][] users,int[] emoticons){ // 최대 가입 수와 최대 판매액을 계산 
        
        int count=0; // 해당 이모티콘 할인율이 적용된 가입 수 
        int earn_t=0; // 해당 이모티콘 할인율이 적용된 판매액 
        
        for(int[] user:users){
            int discount= user[0]; // 할인 기준 40
            int price =user[1]; // 가격 10000 
            int sum=0; 
            
            for(int i=0;i<arr.length;i++){  
                if(arr[i]>=discount){   // 할인 기준 40보다 크거나 같은경우 
                    sum+=(emoticons[i]/100)*(100-arr[i]);  //7000원 40% 할인받아 4200원에 해당 
                }
            }
            
            if(sum>=price){ // 만약 총 금액이 10000보다 많아질경우 
                count++;    // 해당 이모티콘 플러스 서비스 가입 수 증가  
            }
            else{            // 아닐 경우에는 수익을 증가 
                earn_t+=sum; 
            }  
        }

// 할인율에 대해서 가입한 회원과 수익을 지금까지 구한 최대 회원과 최대 수익을 비교하여 최적의 수를 구하기 
        if(count > sign){
            sign=count;
            earn=earn_t;
            return;
        }else if(count == sign){
            if(earn<earn_t){
                earn=earn_t;
            }
        }
    }
    
}

```
