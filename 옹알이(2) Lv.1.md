```java

class Solution {
    public int solution(String[] babbling) {
        int answer = 0;
// ["ayaye", "uuuma", "yeye", "yemawoo", "ayaayaa"]
        for(String a : babbling){
          if(a.contains("ayaaya") || a.contains("yeye") || a.contains("woowoo") || a.contains("mama") )  //연속되어 발음할 수 없음 
          continue;

          if(a.replace("aya"," ")
              .replace("ye"," ")
              .replace("woo"," ")
              .replace("ma"," ")
              .replace(" ","").isEmpty())  //문자열 길이 0일 경우
              answer++;
}
        return answer;
    }
}
