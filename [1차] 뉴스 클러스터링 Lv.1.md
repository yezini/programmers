'''java```

import java.util.*;

class Solution {
    public int solution(String str1, String str2) {
		str1 = str1.toUpperCase(); // 모두 대문자로 
		str2 = str2.toUpperCase();
		
		ArrayList<String> list1 = new ArrayList<>();
		ArrayList<String> list2 = new ArrayList<>();

		ArrayList<String> u = new ArrayList<>(); // 합집합
		ArrayList<String> i = new ArrayList<>(); // 교집합

		// str1 다중 집합 
		for(int c = 0; c < str1.length()-1; c++) { // 5
			char a = str1.charAt(c); // F
			char b = str1.charAt(c+1); // R

			// 문자만
			if(Character.isLetter(a) && Character.isLetter(b)) {
       list1.add(Character.toString(a) + Character.toString(b)); // FR 
			}
		}

		// str2 다중 집합 
		for(int h = 0; h < str2.length()-1; h++) { // 5
			char a = str2.charAt(h); // F
			char b = str2.charAt(h+1); // R

			// 문자만 
			if(Character.isLetter(a) && Character.isLetter(b)) {
		list2.add(Character.toString(a) + Character.toString(b)); // FR
			}
        }

		// 중복 위해 집합 정렬
		Collections.sort(list1); 
		Collections.sort(list2);
		
		// 교집합 
	for(String s : list1) { // FR NC 
     if(list2.remove(s)) {  // 집합1에 집합2가 포함된다면 삭제
				i.add(s);   // 교집합에 추가 
			}
			u.add(s); 
		}
		
		// 합집합 
		for(String s : list2) { // 교집합에서 제외된 것 
			u.add(s); // 나머지 합집합에 추가 
		}
        
		// 자카드 유사도
		double aa = i.size();
		double bb = u.size();

   		double jakard = 0;
	
		if(u.size() == 0)
			jakard = 1;	// 공집합
		else
			jakard = (double) i.size() / (double) u.size();

		return (int) (jakard * 65536);
    }
}


