
import java.util.*;
import java.util.stream.IntStream;

  class Solution {
    public int[] solution(String today, String[] terms, String[] privacies) {
        
        HashMap<String, Integer> term = new HashMap<>(); 
        for(String a : terms){
            String[] b = a.split(" ");      // ["A","6"]
            term.put(b[0], Integer.parseInt(b[1])); //  (A, 6)

}
    ArrayList<Integer> result = new ArrayList<>();
        
     String[] todayDate= today.split("\\."); // ["2022","05","19"]
     int totalDate  = Integer.parseInt(todayDate[0])*12*28 + Integer.parseInt(todayDate[1])*28 + Integer.parseInt(todayDate[2]); 
       
        for(int i=0; i< privacies.length; i++){ // 4
           String[] c = privacies[i].split(" "); // ["2021.05.02", "A"]
           String[] d = privacies[0].split("\\."); // ["2021", "05","02"]
          
            int year = Integer.parseInt(d[0]); // 2021
            int month = Integer.parseInt(d[1]) + term.get(b[1]); // 11
            int day = Integer.parseInt(d[2]); // 2
            
            int total = (year*12*28) + (month*28) + day;

            if(total <= totalDate){
            result.add(i+1);

        }
}
            
           return result.stream().flatMapToInt(x -> IntStream.of(x)).toArray();
     }
}
/*

import java.util.*;
class Solution {
    public int[] solution(String today, String[] terms, String[] privacies) {
        //오늘 날짜에 해당 
        String now = today.replace(".","");//20220519
        int year=Integer.parseInt(now.substring(0,4));//2022
        int month=Integer.parseInt(now.substring(4,6));//05
        int day=Integer.parseInt(now.substring(6,8));//19
        
        int cnt = (year*12*28)+(month*28)+day; //전체 일수 구하기
        
        int[] answer = new int[privacies.length];//4
        
        for(int i=0;i<privacies.length;i++){ //4번 반복
                String[] pri=privacies[i].split(""); //2021.05.02     A
                                                   //2021.07.01    B
           int num=0;
            for(int j=0;j<terms.length;j++){
            String[] ter=terms[j].split(""); //A 6
            if(privacies[1].equals(ter[0])){//약관 종류가 동일해야 하므로 
                num=Integer.parseInt(ter[1]);//6을 정수로 변환
                break;
            }
                //	privacies
               String[] ddd=pri[0].split(".");//2021 05 02
               int y=Integer.parseInt(ddd[0]);//2021
               int m=Integer.parseInt(ddd[1]);//05
               int d=Integer.parseInt(ddd[2]);//02
               
               m=m+num;
               int c=(12*y*28)+(m*28)+(d);
               
              if(c>cnt){
                  //파기해야 할 개인정보면 리스트에 추가
                  answer[i]=i+1;
              } 
        }      
            int a=0;
            for(int w=0;w<answer.length;w++){
                if(answer[w]>0){
                    a++;
                }
            }
           int[] arr=new int[a];
            int index=0;
            for(int q=0;q<answer.length;q++){
                if(answer[q]>0){
                    arr[index]=answer[q];
                    index++;
                }
                
                
            }
        }
        return answer;
    }
}


*/
